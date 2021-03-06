# Responsive design
Modern technology allows users to browse the Internet via multiple devices, such as desktop monitors, mobile phones, tablets, and more. Devices of different screen sizes, however, pose a problem for web developers: how can we ensure that a website is readable and visually appealing across all devices, regardless of screen size?

The answer: *responsive design*! 

Relative units of measurement are a first step towards incorporating responsive design in a website. When combined with more advanced responsive techniques, you can create a seamless user experience regardless of a device's screen size.

# Pixels
Pixels are used to size content to exact dimensions. For example, if you want a div to be exactly 500 pixels wide and 100 pixels tall, then the unit of ```px``` can be used. Pixels, however, are fixed, **hard coded** values meaning that they cannot be altered without modifying the program. When a screen size changes (like switching from landscape to portrait view on a phone), elements sized with pixels can appear too small, overflow the screen, or become completely illegible.

With CSS, you can avoid hard coded measurements and use *relative measurements* instead. Relative measurements offer an advantage over hard coded measurements, as they allow for the proportions of a website to remain intact regardless of screen size or layout.

# Em
Incorporating relative sizing starts by using units other than pixels. One unit of measurement you can use in CSS to create relatively-sized content is the ```em```, written as ```em``` in CSS.

The ```em``` represents the size of the base font being used. For example, if the base font of a browser is 16 pixels (which is normally the default size of text in a browser), then 1 ```em``` is equal to 16 pixels. 2 ```em```s would equal 32 pixels, and so on. If you're interested in sizing elements in comparison to other elements nearby, then the em unit would be better suited for the job.

--example:
```
.splash-section {
  font-size: 18px;
}

.splash-section h1 {
  font-size: 1.5em;
}
```

The example above shows how to use ```em```s without relying on the default font size of the browser. Instead, a base font size (18px) is defined for all text within the ```splash-section``` element. The second CSS rule will set the font size of all ```h1``` elements inside of ```splash-section``` relative to the base font of ```splash-section``` (18 pixels). The resulting font size of ```h1``` elements will be 27 pixels.

# Rem (Root em)
The second relative unit of measurement in CSS is the *rem*, coded as ```rem```. Rem stands for *root em*. It acts similar to em, but instead of checking parent elements to size font, it checks the root element. The root element is the ```<html>``` tag. Most browsers set the font size of ```<html>``` to 16 pixels, so by default rem measurements will be compared to that value. To set a different font size for the root element, you can add a CSS rule. One advantage of using rems is that all elements are compared to the same font size value, making it easy to predict how large or small font will appear. If you are interested in sizing elements consistently across an entire website, the rem measurement is the best unit for the job. 

--example:
```
html {
  font-size: 20px;
}

h1 {
  font-size: 2rem;
}
```

# Percentages 
To size non-text HTML elements relative to their parent elements on the page you can use *percentages*. Percentages are often used to size box-model values, like width and height, padding, border, and margins. When percentages are used to set padding and margin, however, they are calculated based only on the width of the parent element. They can also be used to set positioning properties (top, bottom, left, right).

**Note:** Because the box model includes padding, borders, and margins, setting an element's width to 100% may cause content to overflow its parent container. While tempting, 100% should only be used when content will not have padding, border, or margin.

--example: 
```
.main {
  height: 300px;
  width: 500px;
}

.main .subsection {
  height: 50%;
  width: 50%;
}
```

# Max & Min

When a browser window is narrowed or widened, text can become either very compressed or very spread out, making it difficult to read. Two properties ensure that content is legible by limiting the minimum and maximum widths. You can limit an element with the following properties:  
```min-width``` — ensures a minimum width for an element.
```max-width``` — ensures a maximum width for an element.
```min-height``` — ensures a minimum height for an element's box.
```max-height``` — ensures a maximum height for an element's box

--example: 
 ```
 p {
  min-width: 300px;
  max-width: 600px;
}
```
In the example above, when the browser is resized, the width of paragraph elements will not fall below 300 pixels, nor will their width exceed 600 pixels.

# Auto
When the height of an image or video is set, then its width can be set to ```auto``` so that the media scales proportionally. Reversing these two properties and values will also achieve the same result.

# Scaling background images 

By default, images will repeat. Not have the background image not repeat use:
```
background-repeat: no-repeat;
```
To scale the background image and have it cover the entire background of the element, all while keeping the image in proportion, use: 
```
background-size: cover;
```

# Media Queries
CSS uses *media queries* to adapt a website's content to different screen sizes. With media queries, CSS can detect the size of the current screen and apply different CSS styles depending on the width of the screen. 

--example:
```
@media only screen and (max-width: 480px) {
  body {
    font-size: 12px;
  }
}
```
The media query defines a rule for screens smaller than 480 pixels (approximately the width of many smartphones in landscape orientation).
```@media``` — Keyword that begins a media query rule and instructs the CSS compiler on how to parse the rest of the rule.

```only screen``` — Indicates what types of devices should use this rule. In early attempts to target different devices, CSS incorporated different media types (screen, print, handheld). The rationale was that by knowing the media type, the proper CSS rules could be applied. However, “handheld” and “screen” devices began to occupy a much wider range of sizes and having only one CSS rule per media device was not sufficient. ```screen``` is the media type always used for displaying content, no matter the type of device. The ```only``` keyword is added to indicate that this rule only applies to one media type (```screen```)

```and (max-width : 480px)``` — Media feature that instructs the CSS compiler to apply the CSS styles to devices with a width of 480 pixels or smaller. Media features are the conditions that must be met in order to render the CSS within a media query. **Note:** The ```and``` operator can be used to chain as many media features as necessary.

By using multiple widths and heights, a range can be set for a media query.
```
@media only screen and (min-width: 320px) and (max-width: 480px) {
    /* ruleset for 320px - 480px */
}
```

# Media Queries - Resolution
To target by resolution, we can use the ```min-resolution``` and ```max-resolution``` media features. These media features accept a resolution value in either **dots per inch (dpi)** or **dots per centimeter (dpc)**. 

--example: 
```
@media only screen and (min-resolution: 300dpi) {
    /* CSS for high resolution screens */
}
```
The media query in the example above targets high resolution screens by making sure the screen resolution is at least 300 dots per inch. If the screen resolution query is met, then we can use CSS to display high resolution images and other media.

If only one of multiple media features in a media query must be met, media features can be separated in a **comma separated list**.

--example:
```
@media only screen and (min-width: 480px), (orientation: landscape) {
    /* CSS ruleset */
}
```
In the example above, we used a comma (```,```) to separate multiple rules. The example above requires only one of the media features to be true for its CSS to apply. The ```orientation``` media feature detects if the page has more width than height. If a page is wider, it's considered ```landscape```, and if a page is taller, it's considered ```portrait```.
