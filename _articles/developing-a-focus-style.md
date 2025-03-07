---
title: Developing a focus style for a themable design system
link: https://adhocteam.us/2022/02/08/creating-focus-style-for-themable-design-system/
summary: Making them accessible, themable, and impossible to miss without clashing with your brand.
summary-long:  On a recent project, we had a set of focus styles built into a design system that were inconsistent and ineffective, leading to a not-so-great end user experience.
image: focus-style.png
date: 2022-02-08
home: yes
layout: article
---

Focus styles are visual indicators used to style elements, usually links and form elements, that have been focused by the user, either by “tabbing” using the keyboard or by clicking.

Focus styles help people ~~with low vision conditions, cognitive concerns, or motor impairments~~ identify interactive elements.

## Browser default focus styles

Default browser focus styles aren’t always reliable in the context of your brand theming and color palette. For example, if your brand color palette uses blue and the default browser focus style is also blue then little contrast exists when something is being focused and you run the risk of the focus style blending in with the brand colors.

The default focus styles provided by browsers are typically blue but can differ between each browser, so they’re highly visible in some scenarios, like on a white background, and very hard to notice in other scenarios, like on a blue button.

![Focus styles examples from Google Chrome, Microsoft Edge Mozilla Firefox, and Apple Safari browsers shown on buttons, links and text inputs.](/../assets/images/articles/focus-style-browser-default-847x584.png)

Improving design system focus styles
On a recent project, we had a set of focus styles built into a design system that were inconsistent and ineffective, leading to a not-so-great end user experience. We decided to revisit them to make for a better focus experience throughout the design system.

The inconsistency arose because some elements used the browser default focus styles, like links and buttons, while other elements like text boxes and dropdowns relied on custom focus styles. In some instances, the focus styles were ineffective because the color contrast of the focused style compared to the focused element wasn’t enough to ensure visibility by as many users as possible. In addition, sometimes the focus style lacked a high enough contrast to the page background.

Example of focus styles that were using the browser default and custom focus styles mixed:

![An example of a focus style where the focus on certain elements like a button does not have high enough contrast between the button color and the focus color making it hard to see.](/../assets/images/articles/focus-style-default-mixed-819x124.png)

We also support sub-brands with the design system, and those also had similarly inconsistent and ineffective focus styles. The design system did not provide custom focus styles for all elements so the team created its own additional focus styles resulting in two custom focus styles. This resulted in an inconsistent focus experience and one of the focus styles did not meet color contrast.

Example of sub brand focus styles that were using two different styles for focus styles:

![An example of a focus style where the focus style does not have enough contrast in relation to the background page color making it hard to see.](/../assets/images/articles/focus-style-two-diff-819x123.png)

As we thought about how to create a new focus style for the design system that applied consistently and would be themable for our sub brands, we outlined our guideposts for the work.

## Goals for the improved focus styles

We wanted to create a focus style that would improve the usability and accessibility across the design system and could be easily adopted and customized by design system sub brands.

Specifically that meant:

* We wanted to improve the feature’s usability and accessibility by helping users with attention, short term memory, or executive process limitations discover where the focus is located.
* We wanted to highlight the focus universally for all users while complementing the existing user interface (UI) color palette.
* We wanted to create an intentional focus experience instead of relying on browser defaults.
* We wanted to ensure the design system is accessible beyond compliance with [WCAG 2.1](https://www.w3.org/WAI/WCAG21/Understanding/focus-visible) and be future friendly to [WCAG 2.2](https://www.w3.org/WAI/standards-guidelines/wcag/new-in-22/#2411-focus-appearance-minimum-aa).

## Starting with focus techniques

Before we got into thinking about color choices, we explored various techniques for applying a focus style. This allowed us to then determine which technique had the most flexibility as well as evaluate advantages and disadvantages for each technique. We also wanted to start with techniques so we could align with our stakeholders before moving on to something like colors and design.

We looked at the following:

### Outline

Outline has square edges and does not offer much customization.

![An example of an outline focus style on a button, link and text input on both light and dark backgrounds side by side.](/../assets/images/articles/focus-style-outline-938x220.png)

Customizations:

* Color - sets the color of an element’s outline
* Style - sets the style of an element’s outline (solid, dashed, dotted, etc…)
* Width - sets the thickness of an element’s outline

### Box-shadow
Box-shadow can have the appearance of an outline or border and offers more flexibility than outline or border for customizing.

![An example of a box-shadow focus style on a button, link and text input on both light and dark backgrounds side by side.](/../assets/images/articles/focus-style-box-shadow-938x220.png)

Customizations:

* Color - sets the color of an element’s box-shadow
* Position (X/Y) - sets the horizontal and vertical distance of the box-shadow
* Blur radius - sets the amount of blur to be applied to the box-shadow
* Spread radius - sets the amount the box-shadow will spread
* You can apply multiple box shadows to an element

### Text-decoration underline
Text-decoration underline only works for buttons and links and does not work for form elements such as text inputs or radio buttons.

![An example of a text-decoration underline focus style on a button, link and text input on both light and dark backgrounds side by side.](/../assets/images/articles/focus-style-underline-938x220.png)

Customizations:

* Color - sets the color of decorations
* Line - sets the kind of decoration that is used
* Style - sets the style of the lines specified (solid, dashed, dotted, etc…)
* Thickness - sets the stroke thickness of the decoration line

### Border
Borders can have the appearance of an outline that hugs the element it’s applied to or can appear as an underline if only applying the border to the bottom.

![An example of a border focus style on a button, link and text input on both light and dark backgrounds side by side.](/../assets/images/articles/focus-style-border-938x220.png)

Customizations:

* Color - sets the color of an element’s outline
* Style - sets the style of an element’s outline (solid, dashed, dotted, etc…)
* Width - sets the thickness of an element’s outline
* Border-radius - sets the amount of rounding applied to the corners of an element’s outer border edge

### Background Color
Background color offers the least amount of customization and only offers color as a way to modify it.

![An example of a background color focus style on a button, link and text input on both light and dark backgrounds side by side.](/../assets/images/articles/focus-style-bkg-color-938x220.png)

Customizations:

* Background color - sets the background color of an element

We compared these different techniques against some common scenarios for the design system.

<table class="table" aria-label="Focus techniques compared">
<caption>Focus techniques compared</caption>
    <thead class="table__head">
        <tr>
            <th scope="col" class="table__cell table__cell--head">Scenario</th>
            <th scope="col" class="table__cell table__cell--head text-center" width="15%">Outline</th>
            <th scope="col" class="table__cell table__cell--head text-center" width="15%">Box-shadow</th>
            <th scope="col" class="table__cell table__cell--head text-center" width="15%">Border</th>
            <th scope="col" class="table__cell table__cell--head text-center" width="15%">Text dec underline</th>
            <th scope="col" class="table__cell table__cell--head text-center" width="15%">Bg color</th>
        </tr>
    </thead>
    <tbody class="table__body weight--500">
        <tr>
            <td class="table__cell align-middle weight--600">Doesn't take up the height or width on the page</td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
            <td class="table__cell text-center align-middle text-coral-darkest bkg-light-coral"> Poor </td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Can control spacing from focused element</td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
            <td class="table__cell text-center align-middle text-coral-darkest bkg-light-coral"> Poor </td>
            <td class="table__cell text-center align-middle text-coral-darkest bkg-light-coral"> Poor </td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Works well with Windows High Contrast mode **</td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
            <td class="table__cell text-center align-middle text-yellow-darkest bkg-light-yellow"> Supported </td>
            <td class="table__cell text-center align-middle text-yellow-darkest bkg-light-yellow"> Supported </td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
            <td class="table__cell text-center align-middle text-yellow-darkest bkg-light-yellow"> Supported </td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Consistently applied to all elements</td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
            <td class="table__cell text-center align-middle text-coral-darkest bkg-light-coral"> Poor </td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Honors the border-radius property</td>
            <td class="table__cell text-center align-middle text-coral-darkest bkg-light-coral"> Poor </td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
            <td class="table__cell text-center align-middle text-coral-darkest bkg-light-coral"> Poor </td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Works with letters that have descenders</td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
            <td class="table__cell text-center align-middle text-coral-darkest bkg-light-coral"> Poor </td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">More styling options</td>
            <td class="table__cell text-center align-middle text-coral-darkest bkg-light-coral"> Poor </td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
            <td class="table__cell text-center align-middle text-coral-darkest bkg-light-coral"> Poor </td>
            <td class="table__cell text-center align-middle text-coral-darkest bkg-light-coral"> Poor </td>
            <td class="table__cell text-center align-middle text-coral-darkest bkg-light-coral"> Poor </td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Can use more than one color</td>
            <td class="table__cell text-center align-middle text-coral-darkest bkg-light-coral"> Poor </td>
            <td class="table__cell text-center align-middle text-green-darker bkg-green-quarternary"> Good </td>
            <td class="table__cell text-center align-middle text-coral-darkest bkg-light-coral"> Poor </td>
            <td class="table__cell text-center align-middle text-coral-darkest bkg-light-coral"> Poor </td>
            <td class="table__cell text-center align-middle text-coral-darkest bkg-light-coral"> Poor </td>
        </tr>
    </tbody>
</table>

_** It is common to use border, background color, and box-shadow when creating custom focus styles. However, Windows High Contrast Mode ignores these properties making your focus style invisible in WCHM. This can be fixed by utilizing the default outline property and making it transparent: outline 3px solid transparent. WHCM will override the transparent outline color, making it visible only when high contrast mode is turned on._

Based on these ratings, box-shadow and outline were our top two techniques, but we ultimately selected box-shadow over outline because there were more options for design flexibility like the layering of multiple box-shadows and honoring of the border-radius property.

## Exploring single and double color techniques
Once we selected the box-shadow technique, we then explored the options of using a single color or two colors for the focus styles.

### Using a single color
When you use a single color, it either meets contrast on a light background or meets contrast on a dark background but won’t work well for both. Focus styles that only use one color are not as flexible and resilient because they’re only effective in certain situations, which narrows the range where they would successfully meet contrast ratios.

In this example, the purple focus style meets 4:5.1 contrast on the light background but does not on the dark background:

![An example of a focus style that uses a single color on a button, link and text input on both light and dark backgrounds side by side.](/../assets/images/articles/focus-style-single-color-1047x554.png)

### Using two colors
When you use two colors, the focus will have sufficient contrast against most background colors. This technique ensures sufficient contrast of the focus indicator when viewed against different backgrounds because both a light and dark color are used in the focus style. We took inspiration from Chromium and the Slack application which use a two color approach to focus styles as well.

In this example, the purple in the focus style meets 4:5.1 contrast on the light background and the white focus style color meets 4:5.1 contrast on the dark background:

![An example of a focus style that uses a 2 colors on a button, link and text input on both light and dark backgrounds side by side.](/../assets/images/articles/focus-style-two-color-1047x554.png)

We selected the two color approach due to the flexibility of the focus style working in more situations.

## Focus style color exploration
Now that we had our technique and number of colors that we were going to use for the focus styles, we began to look into what color options would work well for the design system and explored options that would fit into both sub brand themes.

We explored color options that were already in use in the brand palettes as well as new color choices that would compliment the brand. This helped us get a sense of what types of colors would compliment the design system palette and also meet color contrast ratios for focus styles.

We wanted to make sure the color selected met at least 3.1 color contrast on a white background and set a stretch goal for the color to meet 4:5.1 color contrast on white. We evaluated multiple colors against these requirements and goals and came up with the following concepts.



<table class="table" aria-label="Focus techniques compared">
<caption>Existing colors from sub brands</caption>
    <thead class="table__head">
        <tr>
            <th scope="col" class="table__cell table__cell--head" width="40%">Color name</th>
            <th scope="col" class="table__cell table__cell--head text-center" width="15%">Color swatch</th>
            <th scope="col" class="table__cell table__cell--head text-center">Meets 4:5.1 on white</th>
            <th scope="col" class="table__cell table__cell--head text-center">Meets 3.1 on white</th>
        </tr>
    </thead>
    <tbody class="table__body">
        <tr>
            <td class="table__cell align-middle weight--600">Secondary orange #D44116</td>
            <td class="table__cell align-middle" style="background-color: #D44116;"
                aria-label="Cell colored with #D44116"></td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Accent orange #EC6841</td>
            <td class="table__cell align-middle" style="background-color: #EC6841;"
                aria-label="Cell colored with #EC6841"></td>
            <td class="table__cell align-middle text-center weight--600 text-coral-darker bkg-light-coral">No</td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Illustration orange #EB6941</td>
            <td class="table__cell align-middle" style="background-color: #EB6941;"
                aria-label="Cell colored with #EB6941"></td>
            <td class="table__cell align-middle text-center weight--600 text-coral-darker bkg-light-coral">No</td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Current gold #F1AD15</td>
            <td class="table__cell align-middle" style="background-color: #F1AD15;"
                aria-label="Cell colored with #F1AD15"></td>
            <td class="table__cell align-middle text-center weight--600 text-coral-darker bkg-light-coral">No</td>
            <td class="table__cell align-middle text-center weight--600 text-coral-darker bkg-light-coral">No</td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Current teal #146a5d</td>
            <td class="table__cell align-middle" style="background-color: #146a5d;"
                aria-label="Cell colored with #146a5d"></td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Current blue #3E94CF</td>
            <td class="table__cell align-middle" style="background-color: #3E94CF;"
                aria-label="Cell colored with #3E94CF"></td>
            <td class="table__cell align-middle text-center weight--600 text-coral-darker bkg-light-coral">No</td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
        </tr>
    </tbody>
</table>

<table class="table" aria-label="Focus techniques compared">
<caption>Possible new colors</caption>
    <thead class="table__head">
        <tr>
            <th scope="col" class="table__cell table__cell--head" width="40%">Color name</th>
            <th scope="col" class="table__cell table__cell--head text-center" width="15%">Color swatch</th>
            <th scope="col" class="table__cell table__cell--head text-center">Meets 4:5.1 on white</th>
            <th scope="col" class="table__cell table__cell--head text-center">Meets 3.1 on white</th>
        </tr>
    </thead>
    <tbody class="table__body">
        <tr>
            <td class="table__cell align-middle weight--600">Focus coral #CD635B</td>
            <td class="table__cell align-middle" style="background-color: #CD635B;"
                aria-label="Cell colored with #CD635B"></td>
            <td class="table__cell align-middle text-center weight--600 text-coral-darker bkg-light-coral">No</td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Focus orange #DF6D52</td>
            <td class="table__cell align-middle" style="background-color: #DF6D52;"
                aria-label="Cell colored with #DF6D52"></td>
            <td class="table__cell align-middle text-center weight--600 text-coral-darker bkg-light-coral">No</td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Focus gold #F6AE2D </td>
            <td class="table__cell align-middle" style="background-color: #F6AE2D;"
                aria-label="Cell colored with #F6AE2D"></td>
            <td class="table__cell align-middle text-center weight--600 text-coral-darker bkg-light-coral">No</td>
            <td class="table__cell align-middle text-center weight--600 text-coral-darker bkg-light-coral">No</td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Focus tangerine #EEA243</td>
            <td class="table__cell align-middle" style="background-color: #EEA243;"
                aria-label="Cell colored with #EEA243"></td>
            <td class="table__cell align-middle text-center weight--600 text-coral-darker bkg-light-coral">No</td>
            <td class="table__cell align-middle text-center weight--600 text-coral-darker bkg-light-coral">No</td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Focus sand #AF6118</td>
            <td class="table__cell align-middle" style="background-color: #AF6118;"
                aria-label="Cell colored with #AF6118"></td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Focus blue #3F84E5</td>
            <td class="table__cell align-middle" style="background-color: #3F84E5;"
                aria-label="Cell colored with #3F84E5"></td>
            <td class="table__cell align-middle text-center weight--600 text-coral-darker bkg-light-coral">No</td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Focus green #1B998B</td>
            <td class="table__cell align-middle" style="background-color: #1B998B;"
                aria-label="Cell colored with #1B998B"></td>
            <td class="table__cell align-middle text-center weight--600 text-coral-darker bkg-light-coral">No</td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Focus elm green #1B7869</td>
            <td class="table__cell align-middle" style="background-color: #1B7869;"
                aria-label="Cell colored with #1B7869"></td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Focus deep sea green #008853</td>
            <td class="table__cell align-middle" style="background-color: #008853;"
                aria-label="Cell colored with #008853"></td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Focus eggplant #BD13B8</td>
            <td class="table__cell align-middle" style="background-color: #BD13B8;"
                aria-label="Cell colored with #BD13B8"></td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Focus orchid #94679A</td>
            <td class="table__cell align-middle" style="background-color: #94679A;"
                aria-label="Cell colored with #94679A"></td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Focus rose #883955</td>
            <td class="table__cell align-middle" style="background-color: #883955;"
                aria-label="Cell colored with #883955"></td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
        </tr>
        <tr>
            <td class="table__cell align-middle weight--600">Focus magenta #AF3B6E</td>
            <td class="table__cell align-middle" style="background-color: #AF3B6E;"
                aria-label="Cell colored with #AF3B6E"></td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
            <td class="table__cell align-middle text-center weight--600 text-green-darker bkg-green-quarternary">Yes</td>
        </tr>
    </tbody>
</table>

For the design system and on of the the sub brand themes, we selected a focus eggplant color of #BD13B8, which meets both 3.1 and 4:5.1 color contrast on white backgrounds. In addition, the focus eggplant color compliments the current design system color palette and stands out while not being too distracting.

For our other sub brand, we selected a focus orange color of #DD3603, which also meets both 3.1 and 4:5.1 color contrast on white backgrounds, compliments the sub brand color palette, and can be seen as an accent color in illustrations throughout the site and applications.

If you’d like to do a similar comparison for your design system, there are a lot of great accessible color tools out there. Here are a few that we used:

* [Accessible color palette builder](https://line47.com/accessible-color-matrix)
* [Colors that look and work great for everyone](https://color.review/check/FEDC2A-5A3B5D)
* [Tanaguru contrast-finder](https://contrast-finder.tanaguru.com/)
* [Color contrast checker, analyser and color suggestions](https://polypane.app/color-contrast/#fg=F1AD15&bg=ffffff&level=aaa&format=hex)
* [WebAIM contrast checker](https://webaim.org/resources/contrastchecker/)
* [EightShapes contrast grid](/https://contrast-grid.eightshapes.com/?version=1.1.0&background-colors=&foreground-colors=%23FFFFFF%2C%20White%0D%0A%23F2F2F2%0D%0A%23DDDDDD%0D%0A%23CCCCCC%0D%0A%23888888%0D%0A%23404040%2C%20Charcoal%0D%0A%23000000%2C%20Black%0D%0A%232F78C5%2C%20Effective%20on%20Extremes%0D%0A%230F60B6%2C%20Effective%20on%20Lights%0D%0A%23398EEA%2C%20Ineffective%0D%0A&es-color-form__tile-size=compact&es-color-form__show-contrast=aaa&es-color-form__show-contrast=aa&es-color-form__show-contrast=aa18&es-color-form__show-contrast=dnp)

We were nearing the finish line and during our explorations, testing, and finalizing of the focus style for the design system and its sub brands we found an issue that we needed to address before officially releasing the update. This issue was that multi-line links with the new box-shadow focus style did not perform well from a design or readability standpoint. Box shadow offers more options when it comes to styling but is not as functional as using the outline property. Here is what we were seeing when using the double box-shadow on multi-line links, yuck!

![An example of a link focus style on both light and dark backgrounds side by side when the focus style uses a box-shadow.](/../assets/images/articles/focus-style-link-shadow-493x145.png)

We tried a few different options and decided to use the outline property for links in addition to a background color so that we can still have one focus style that works for both light and dark backgrounds.

![An example of a link focus style on both light and dark backgrounds side by side when the focus style uses an outline and a background color.](/../assets/images/articles/focus-style-link-outline-499x152.png)

## Our new focus styles
After exploring 18 different techniques and 19 different color options, we felt we had reached our goal of creating a focus style that will improve the usability and accessibility across the design system and could be easily adopted and customized by the design system’s sub brands.

![An example of double box-shadow and outline focus styles on both light and dark backgrounds side by side on multiple types of form and interactive elements.](/../assets/images/articles/focus-style-final-791x810.png)

The box-shadow technique provided us enough flexibility by using multiple colors, did not take up any height or width on the page, was consistently applied to all elements, honors the border-radius property, and works well with descending letters.

Our final focus color was Focus eggplant - #BD13B8. We expect the majority of focus styles will be seen on light or white backgrounds. Therefore, we prioritized choosing colors that meet contrast on lighter backgrounds. This color also works for our sub brands if left unthemed. However, each sub brand can select its own color to better serve the people who interact with its components every day.

We stayed away from teals and blues for the focus color because they’re a dominant hue in the design system already.

## Meeting WCAG guidelines
Our new focus style would meet both current and potential WCAG guidelines.

[1.4.1 Use of Color (WCAG 2.0)](https://www.w3.org/WAI/WCAG21/Understanding/use-of-color.html)
Using the outline around elements means we’re not relying on color alone to communicate the focus state.

[1.4.11 Non-text Contrast (WCAG 2.1)](https://www.w3.org/WAI/WCAG21/Understanding/non-text-contrast.html)
The use of multiple colors means that in most situations, the color contrast will be above 3:1 for the focused state.

[2.4.7 Focus Visible (WCAG 2.0)](https://www.w3.org/WAI/WCAG21/Understanding/focus-visible.html)
We meet this by supplying our own highly visible focus indicator.

[2.4.11 Focus Appearance Minimum (WCAG 2.2)](https://www.w3.org/WAI/WCAG22/Understanding/focus-appearance-minimum.html)
While WCAG 2.2 isn’t finalized yet, we’re looking to the future.

* The outlines wrap around entire elements and are at least 2 pixels thick meaning the focus state meets “minimum area” requirements, which define how much space a focus indicator should take up to be noticeable.
* The use of eggplant and white means we meet a contrast ratio of at least 3:1 between the colors in the focused and unfocused states.
* The choice of colors and outline thickness means we meet a contrast ratio of at least 3:1 against adjacent colors in the focused component, plus the contrasting area has a thickness of at least 2 CSS pixels.

## How we set up theming
### Focus style variables
We created two focus style variables, one to be used for the inner box-shadow and one to be used for the outer box-shadow. This allows sub brands to easily customize their focus styles to fit with their brand.

* `$color-focus-light` sets the inner box-shadow for the focus styles.
* `$color-focus-dark` sets the outer box-shadow for the focus styles. This color should pass a 3.1 contrast ratio on white or light backgrounds.

### Using focus styles on custom components
We created a mixin to use for easily adding focus styles to custom components that are not in the design system and might need their own focus state styles.

The mixin `@include focus-styles;` can be used to apply the focus styles consistently without needing to write custom styles in an application or product.

Example:

```css
.customButton:focus {
  @include focus-styles;
}
```

The focus-styles mixin applies the following styles for the box-shadow. In addition, we’re adding outline and outline offset to support Windows high contrast mode.

```SCSS
box-shadow: 0 0 0 3px $color-focus-light, 0 0 4px 6px $color-focus-dark;
// Add support for Windows High Contrast Mode (WHCM)
// The transparent color only shows when WHCM is triggered
outline: 3px solid transparent;
outline-offset: 3px;
```

We’re currently in the process of deploying our new focus styles and feel confident that this update will result in a more consistent, more accessible, and more themable focus style for the design system and its sub brands.