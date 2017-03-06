# Aspect Ratio Via Attribute Selector

A module for applying a desired aspect ratio to html elements via CSS.

This pure CSS solution&mdash;based on the “[padding hack](https://alistapart.com/article/creating-intrinsic-ratios-for-video)”&mdash;is meant to style a box with a specific aspect ratio regardless of its content.

This is particularely useful to **prevent page reflow**, when media push content further down the page as they load (read “[Preventing Reflow](http://cssmojo.com/aspect-ratio-using-custom-properties-and-calc/)”).

## Features
   
   * It supports boxes styled with a `min-width` or a `max-width`
   * It accepts aspect ratios in a variety of formats
   * It requires a single custom property (no `class`)
   * It allows to specify the `@width` and `@height` of images
   * It works with videos, iframes, etc.

## Browser Support

This works in [browsers that support custom properties](http://caniuse.com/#feat=css-variables); it degrades "silently" in those that don’t.

## Installation

```
npm install aspect-ratio-via-attribute-selector --save-dev
```

### Vanilla CSS

There are 3 things you can do:

   * Add the content of [aspect-ratio-via-attribute-selector.css](https://github.com/thierryk/aspect-ratio-via-css/blob/master/aspect-ratio-via-attribute-selector/aspect-ratio-via-attribute-selector.css) to your styles sheet
   * Use `@import` to import the file from unpkg (used as a CDN):
   
   ```css
   @import https://unpkg.com/aspect-ratio-via-attribute-selector@1/aspect-ratio-via-attribute-selector.css;
   ```
   
   * Use `<link>` to import the file from unpkg (used as a CDN):
   
   ```html
   <link href="https://unpkg.com/aspect-ratio-via-attribute-selector@1/aspect-ratio-via-attribute-selector.css" />
   ```
   
## Usage

### Including A Image

The use of the `width` and `height` attributes on the image is optional

```html
<div style="--aspect-ratio:600/400;">
  <img Width="600" height="400" src="pic.jpg" alt="">
</div>
```

### Including A Video Or Iframe

``` html
<div style="--aspect-ratio:16/9">
  <iframe src="video.mp4"  
          frameborder="0">
  </iframe>
</div>
```

### Sans `<img>`

You can style the background of a box using `background-size` to make sure the background image is sized according to the aspect ratio you have chosen

``` html
<div style="--aspect-ratio:600/400;background:url(pic.jpg);background-size:cover;"></div>
```

**NOTE**: such boxes collapse in browsers that do not support custom properties since there is no content to give the box a height.

## Ratios

Ratios may be entered in a variety of formats. They are the value of the custom property: `—aspect-ratio`

### Dimensions

`400/300` is the `width` and `height` of the image. 

``` html
<div style="--aspect-ratio:400/300;">
  <img src="pic.jpg" 
       alt="">
</div>
```

### Fraction

Ratios like `4/3`, `16/9`, etc.

``` html
<div style="width:20em;--aspect-ratio:4/3;">
  <img src="pic.jpg" 
       alt="">
</div>
```

### Decimal Representation

For example: `400 / 300 = 1.3333`

``` html
<div style="width:50%;--aspect-ratio:1.3333;">
  <img src="pic.jpg" 
       alt="">
</div>
```

___

**IMPORTANT**: If you care about performance, know that there is another version of this module that relies on `class` selector (instead of `attribute` selector).
