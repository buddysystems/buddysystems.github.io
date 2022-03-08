# Home Page Code Review (3/4/2022)

**Main developer**: Elijah Smith (@elijahquentin)

**Supporting developers**: None

**Reviewer**: Connor Kildare (@ckildare)

## Feature Requirements

Implement the UI for the home page of the website to follow the design given by [the Home Page Design document](../design-documents/HomePageDesign.png)

Specifically, this should be done in plain HTML/CSS, with minimal JS if required.

**Supporing documents**:

-   [Home Page Design](../design-documents/HomePageDesign.png)
-   [Branding guidelines](../design-documents/branding.md)

## Review

### Primary Issues

None (:

### Style

-   CSS class names should be `kebab-case`
-   Try to use units that are not `px` as thay are difficult to implement in responsive degins.
-   Responsive design is preferred to support a range of devices. You can incorporate this by utilising a grid model that can be found in the Axel Wilson prject at the bottom of the page. Not a huge issue, but should be considered at some point in the design process.
 
The code for a grid model would look like this:

```css
@media only screen and (min-width: 600px) {
    .col-s-1 {
        width: 8.33%;
    }
    .col-s-2 {
        width: 16.66%;
    }
    .col-s-3 {
        width: 25%;
    }
    .col-s-4 {
        width: 33.33%;
    }

    ...
```

The media queries are used to communicate with the device, in this case to determine how large the screen size is and create partitions of different column amounts and sizes with respect to the device size. This media query is meant for a tablet device and the partitions for these ratios are meant to support 12 columns. The HTML implementation would look like the following:

```html
<div className="row">
            <div className="col-8 col-s-8">
```

The `rows` are used to display blocks of elements vertically, then `columns` are displayed within the rows. In this case, there is one row with elements that will display inthe first 8 columns out of 12 on the page. `col-8` is in reference to one [artition] of media queries for a deivce such as a tablet, and the `col-s-8` is in reference to a partition for a tablet.

-   Some shared elements between text such as `font-family: 'Source Sans Pro', sans-serif;` can be put in the CSS all selector (`*`) or a CSS class for text to avoid DRY.

-   Classes such as `HeaderandNav` have many similar CSS styles that can be coralled into one or a few classes to avoid DRY.

### Other Notes

File names and organization could be improved to better understand the contents.

The rest of these notes are more picky, personal preference items that are not incredibly important.

The HTML and CSS files look cleaner without an abundance of whitespace between lines. I also like to separate different section of a CSS file like so:

```css
/*-----------------------------------------------------------------------------------------------------------------------*/
```

The color sheme for the naviation tabs are difficult to read due tothe bright blue and white. More contrasting colors could improve the readability of the tab names.

I usually like when nav bar names do not have the underlining link with them, and the css `:hover` selctor can be used to make a button change when the user mouses over it. An example of this in use would be:

```css
img {
    max-width: 70%;
    max-height: 70%;
}

img:hover {
    max-width: 70%;
    max-height: 70%;
}
'''