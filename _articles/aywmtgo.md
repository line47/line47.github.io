---
title: AYWMTGO
summary: An interactive teaser for the upcoming Line 47 release.
image: 
date: 2025-03-12
layout: none 
featured: false
published: true
---

<head>
  <meta charset="UTF-8" />
  <title>L47 / AYWMTGO</title>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      background: white;
      overflow: hidden;
    }
    canvas {
      display: block;
      background: white;
    }
    video {
      display: none;
    }
    #cc-controls {
      position: fixed;
      bottom: 0;
      width: 100%;
      z-index: 10;
      background: white;
      padding: 10px;
      border: 1px solid #ccc;
      font-family: monospace;
      font-size: 14px;
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 12px;
    }
    #cc-controls label {
      display: flex;
      align-items: center;
      gap: 6px;
    }
    #cc-controls button {
      padding: 6px 12px;
      font-family: monospace;
      font-size: 14px;
      background: #fff;
      border: 1px solid #ccc;
      cursor: pointer;
    }
  </style>
</head>

<body>
  <!-- Canvas for visuals -->
  <canvas id="visualizer"></canvas>

  <!-- Hidden webcam input -->
  <video id="webcam" autoplay muted playsinline></video>

  <!-- MIDI control panel -->
  <div id="cc-controls">
    <label>CC33 Dot Size:
      <input type="range" id="cc33" min="0" max="127" value="100">
      <span id="cc33-val">100</span>
    </label>
    <label>CC34 Grid Res:
      <input type="range" id="cc34" min="0" max="127" value="60">
      <span id="cc34-val">60</span>
    </label>
    <label>CC35 Shape Morph:
      <input type="range" id="cc35" min="0" max="127" value="0">
      <span id="cc35-val">0</span>
    </label>

    <!-- Control buttons -->
    <button id="setDefaultsBtn">Reset</button>
    <button id="screenshotBtn">Save Screenshot</button>
  </div>

  <!-- JavaScript functionality -->
  <script>
    // Variables and canvas setup
    const canvas = document.getElementById("visualizer");
    const ctx = canvas.getContext("2d");
    const video = document.getElementById("webcam");
    const offscreen = document.createElement("canvas");
    const offCtx = offscreen.getContext("2d");
    let videoAspectRatio = 16 / 9;

    // MIDI CC Values
    let midiValues = [85, 111, 0, ...new Array(13).fill(0)];
    const isPhone = /Mobi|Android/i.test(navigator.userAgent) || window.innerWidth < 480;
    if (isPhone) midiValues[1] = 50;

    // Phrase reveal variables
    const phrase = "AS YOU WERE MEANT TO GO ON";
    const letterIndices = [...phrase].map((c, i) => c !== " " ? i : null).filter(i => i !== null);
    let revealTimers = new Array(letterIndices.length).fill(0);
    let revealedFlags = new Array(letterIndices.length).fill(false);
    let glitchFrames = new Array(letterIndices.length).fill(0);
    let glitchChars = new Array(letterIndices.length).fill('');
    let audioLevel = 0;
    let wasAboveThreshold = false;
    let lines = wrapPhraseIntoLines(phrase);
    let backgroundShapes = [];

    // MIDI Controls
    function setupCCSliders() {
      const sliders = ["cc33", "cc34", "cc35"];
      sliders.forEach((id, index) => {
        const slider = document.getElementById(id);
        const display = document.getElementById(`${id}-val`);
        slider.addEventListener("input", () => {
          midiValues[index] = parseInt(slider.value);
          display.textContent = slider.value;
        });
      });
    }

    // Reset Button
    document.getElementById("setDefaultsBtn").addEventListener("click", () => {
      [85, 111, 0].forEach((val, i) => {
        midiValues[i] = val;
        const id = `cc${33 + i}`;
        document.getElementById(id).value = val;
        document.getElementById(`${id}-val`).textContent = val;
      });
    });

    // Screenshot
    document.getElementById("screenshotBtn").addEventListener("click", () => {
      const screenshotCanvas = document.createElement("canvas");
      screenshotCanvas.width = canvas.width;
      screenshotCanvas.height = canvas.height;
      const scCtx = screenshotCanvas.getContext("2d");
      scCtx.fillStyle = "#fff";
      scCtx.fillRect(0, 0, canvas.width, canvas.height);
      scCtx.drawImage(canvas, 0, 0);
      const link = document.createElement("a");
      link.download = `L47_AYWMTGO_${Date.now()}.png`;
      link.href = screenshotCanvas.toDataURL("image/png");
      link.click();
    });

    // Wraps phrase into multiple lines based on device
    function wrapPhraseIntoLines(phrase) {
      const isPhone = /Mobi|Android/i.test(navigator.userAgent) || window.innerWidth < 600;
      if (isPhone) return ["AS YOU", "WERE", "MEANT", "TO GO ON"];
      const words = phrase.split(" ");
      const lines = [];
      for (let i = 0; i < words.length;) {
        const n = 2 + Math.floor(Math.random() * 2);
        lines.push(words.slice(i, i + n).join(" "));
        i += n;
      }
      return lines;
    }

    // Shape drawing based on CC35
    function drawMorphedShape(ctx, cx, cy, size, morph) {
      ctx.beginPath();
      if (morph <= 0) ctx.rect(cx - size / 2, cy - size / 2, size, size);
      else if (morph >= 1) {
        ctx.moveTo(cx, cy - size / 2);
        ctx.lineTo(cx - size / 2, cy + size / 2);
        ctx.lineTo(cx + size / 2, cy + size / 2);
        ctx.closePath();
      } else {
        const inv = 1 - morph;
        const interp = (a, b) => inv * a + morph * b;
        const p1 = [cx, cy - size / 2];
        const p2 = [cx - size / 2, cy + size / 2];
        const p3 = [cx + size / 2, cy + size / 2];
        ctx.moveTo(interp(cx - size / 2, p1[0]), interp(cy - size / 2, p1[1]));
        ctx.lineTo(interp(cx + size / 2, p2[0]), interp(cy - size / 2, p2[1]));
        ctx.lineTo(interp(cx + size / 2, p3[0]), interp(cy + size / 2, p3[1]));
        ctx.lineTo(interp(cx - size / 2, p1[0]), interp(cy + size / 2, p1[1]));
        ctx.closePath();
      }
      ctx.fill();
    }

    // Halftone drawing using webcam input
    function drawHalftone() {
      const cols = 20 + Math.floor((midiValues[1] / 127) * 140);
      const aspect = canvas.width / canvas.height;
      const rows = Math.floor(cols / aspect);
      offscreen.width = cols;
      offscreen.height = rows;
      const videoAR = video.videoWidth / video.videoHeight;
      const targetAR = cols / rows;
      let sx = 0, sy = 0, sw = video.videoWidth, sh = video.videoHeight;
      if (videoAR > targetAR) {
        sw = video.videoHeight * targetAR;
        sx = (video.videoWidth - sw) / 2;
      } else {
        sh = video.videoWidth / targetAR;
        sy = (video.videoHeight - sh) / 2;
      }
      offCtx.drawImage(video, sx, sy, sw, sh, 0, 0, cols, rows);
      const imageData = offCtx.getImageData(0, 0, cols, rows).data;
      const dotSpacingX = canvas.width / cols;
      const dotSpacingY = canvas.height / rows;
      const dotScale = 0.2 + (midiValues[0] / 127) * 2.8;
      for (let y = 0; y < rows; y++) {
        for (let x = 0; x < cols; x++) {
          const i = (y * cols + x) * 4;
          const brightness = (imageData[i] + imageData[i + 1] + imageData[i + 2]) / 3;
          const size = (1 - brightness / 255) * Math.min(dotSpacingX, dotSpacingY) * 0.5 * dotScale;
          const cx = x * dotSpacingX;
          const cy = y * dotSpacingY;
          ctx.fillStyle = "rgba(0, 0, 0, 0.5)";
          drawMorphedShape(ctx, cx, cy, size, midiValues[2] / 127);
        }
      }
    }

    // Dynamic letter animation
    function drawLine47Text() {
      const fontSize = /Mobi|Android/i.test(navigator.userAgent) || window.innerWidth < 600 ? 150 : Math.floor(canvas.width * 0.06);
      const spacing = /Mobi|Android/i.test(navigator.userAgent) || window.innerWidth < 600 ? 98 : canvas.width * 0.04;
      ctx.save();
      ctx.textAlign = "start";
      ctx.textBaseline = "middle";
      ctx.font = `${fontSize}px 'Lucida Console', monospace`;
      const audioActive = audioLevel > 50;
      if (audioActive && !wasAboveThreshold) {
        const candidates = letterIndices.filter((_, i) => !revealedFlags[i] && revealTimers[i] === 0);
        if (candidates.length > 0) {
          const chosen = candidates[Math.floor(Math.random() * candidates.length)];
          revealTimers[letterIndices.indexOf(chosen)] = 90;
        }
      }
      wasAboveThreshold = audioActive;
      let charIndex = 0;
      const lineHeight = fontSize * 1.2;
      const startY = canvas.height / 2 - (lines.length * lineHeight) / 2 + lineHeight / 2;
      lines.forEach((line, lineNum) => {
        const y = startY + lineNum * lineHeight;
        for (let i = 0; i < line.length; i++) {
          const char = line[i];
          if (char === " ") continue;
          const x = canvas.width * 0.1 + i * spacing;
          const idx = charIndex;
          if (revealTimers[idx] > 0) {
            revealTimers[idx]--;
            if (revealTimers[idx] > 60) {
              if (glitchFrames[idx] % 5 === 0) {
                glitchChars[idx] = String.fromCharCode(33 + Math.floor(Math.random() * 94));
              }
              glitchFrames[idx]++;
              ctx.fillStyle = "rgba(0,0,0,0.5)";
              ctx.fillText(glitchChars[idx], x, y);
            } else if (revealTimers[idx] > 30) {
              revealedFlags[idx] = true;
              ctx.fillStyle = "black";
              ctx.fillText(char, x, y);
            } else {
              ctx.fillStyle = "rgba(0,0,0,0.7)";
              ctx.fillText("▓", x, y);
            }
          } else if (revealedFlags[idx]) {
            ctx.fillStyle = "black";
            ctx.fillText(char, x, y);
          } else {
            ctx.fillStyle = "rgba(0,0,0,0.7)";
            ctx.fillText("▓", x, y);
          }
          charIndex++;
        }
      });
      ctx.restore();
    }

    // Draw loop
    function draw() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      if (video.readyState === video.HAVE_ENOUGH_DATA) {
        drawHalftone();
        drawLine47Text();
      }
      requestAnimationFrame(draw);
    }

    // Initialize webcam and audio
    function startWebcamAndAudio() {
      navigator.mediaDevices.getUserMedia({ video: true, audio: true })
        .then(stream => {
          video.srcObject = stream;
          video.addEventListener("loadedmetadata", () => {
            video.play();
            const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
            const analyser = audioCtx.createAnalyser();
            analyser.fftSize = 256;
            const dataArray = new Uint8Array(analyser.frequencyBinCount);
            audioCtx.createMediaStreamSource(stream).connect(analyser);
            const updateAudio = () => {
              analyser.getByteFrequencyData(dataArray);
              audioLevel = dataArray.reduce((a, b) => a + b, 0) / dataArray.length;
              requestAnimationFrame(updateAudio);
            };
            updateAudio();
            requestAnimationFrame(draw);
          });
        })
        .catch(err => alert("Webcam error: " + err.message));
    }

    // MIDI Input setup
    function onMIDISuccess(midiAccess) {
      for (const input of midiAccess.inputs.values()) {
        input.onmidimessage = onMIDIMessage;
      }
    }

    function onMIDIMessage(event) {
      const [status, cc, value] = event.data;
      if (status === 176 && cc >= 33 && cc <= 48) {
        const idx = cc - 33;
        midiValues[idx] = value;
        const slider = document.getElementById(`cc${cc}`);
        const label = document.getElementById(`cc${cc}-val`);
        if (slider && label) {
          slider.value = value;
          label.textContent = value;
        }
      }
    }

    function onMIDIFailure() {
      console.warn("❌ MIDI access failed");
    }

    // Resize and initialize
    window.addEventListener("resize", resizeCanvas);
    function resizeCanvas() {
      const isPhone = /Mobi|Android/i.test(navigator.userAgent) || window.innerWidth < 600;
      const aspectRatio = isPhone ? 9 / 16 : videoAspectRatio;
      const windowAspect = window.innerWidth / window.innerHeight;
      if (windowAspect > aspectRatio) {
        canvas.height = window.innerHeight;
        canvas.width = canvas.height * aspectRatio;
      } else {
        canvas.width = window.innerWidth;
        canvas.height = canvas.width / aspectRatio;
      }
      canvas.style.position = "absolute";
      canvas.style.left = `${(window.innerWidth - canvas.width) / 2}px`;
      canvas.style.top = `${(window.innerHeight - canvas.height) / 2}px`;
      lines = wrapPhraseIntoLines(phrase);
    }

    // Start everything
    resizeCanvas();
    setupCCSliders();
    startWebcamAndAudio();
    navigator.requestMIDIAccess().then(onMIDISuccess, onMIDIFailure);
  </script>
</body>