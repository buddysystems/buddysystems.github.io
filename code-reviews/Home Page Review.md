# Home Page Code Review (3/4/2022)

**Main developer**: Elijah Smith (@elijahquentin)

**Supporting developers**: None

**Reviewer**: AJ Richerson (@CodeCricut)

## Feature Requirements

Implement the UI for the home page of the website to follow the design given by [the Home Page Design document](../design-documents/HomePageDesign.png)

Specifically, this should be done in plain HTML/CSS, with minimal JS if required.

**Supporing documents**:

-   [Home Page Design](../design-documents/HomePageDesign.png)
-   [Branding guidelines](../design-documents/branding.md)

## Review

### Primary Issues

None

### Style

-   CSS class names should be `kebab-case`
-   Remove unnecessary comments
-   Prefer units like `rem` and `em` for text-size over `px` and `%` (in order to support high-def displays and better scaling)
-   Avoid targeting element types with specific styles

For example, there is an `img` style which shrinks all images, a behavior we don't want and might confuse developers in the future.

-   Not all style selectors must have their entire heirarchy in the selector

For example, given the following HTML

```html
<div class="nav">
    <div class="links">
        <a href="..." class="my-link">...</a>
        <!-- ... -->
    </div>
</div>
```

You can style `my-link` like so:

```css
.my-link {
    ...;
}
```

instead of

```
.nav .links .my-link
```

This has the benefit of being less fragile: we can change the structure/class heirarchy without
breaking the nested styles.

-   More descriptive alternative accessibility values (i.e. `alt` should have human readable description of image)
-   Add global font-family styles, remove other font-family styles unless overriding global style
-   Apply the font-family in the associated [brand document](../design-documents/branding.md)
-   Prefer CSS variables for colors, especially repeated brand colors

Instead of typing styles like `background: #453f8f`. create CSS variables like so and reference them:

```css
:root {
    --brand-main: #453f8f;
}

... .my-element {
    background: var(--brand-main);
}
```

-   Preemptively add CSS variables for brand colors in the [brand document](../design-documents/branding.md)

### Other Notes

One thing that I noticed about the website was that it doesn't have an associated icon which shows in the browser tab. This wasn't part of the requirements but I have created Issue #1 to address it.

This wasn't mentioned as a requirement, but one implicit fact of modern website design is that is should be resopnsive. I don't believe we are going to make the site responsive at this time, but it's something worth researching if you are interested.

The theme is subject to change obviously, but I would note that the white links in the nav are
hard to read agains the light blue background.
