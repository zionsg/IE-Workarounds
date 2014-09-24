### IE workarounds for CSS

In general, issues are sorted according to the CSS property in alphabetical order.
<br /><hr />
**Issue:** Unable to show vertical scrollbar always using overflow-y:scroll.<br />
**Version:** IE10<br />
**Url:** http://msdn.microsoft.com/en-us/library/ie/hh771902(v=vs.85).aspx<br />
**Cause:** Vertical scrollbar appears as overlay<br />
**Workaround:**<br />
```
html {
  overflow-y: scroll;
  -ms-overflow-style: scrollbar; /* specific to IE 10 */
}
```
<br /><hr />
**Issue:** CSS3 Media Queries not supported.<br />
**Version:** IE8 and below<br />
**Url:** https://github.com/scottjehl/Respond<br />
**Cause:** No support<br />
**Workaround:**<br />
Use Respond.js (see Url)
```
<!--[if lte IE 8]>
  <script src="respond.min.js"></script>
<![endif]-->
```
<br /><hr />
**Issue:** display:inline-block does not align horizontally.<br />
**Version:** IE7 and below<br />
**Url:** http://uncorkedstudios.com/2011/12/12/how-to-fix-the-ie7-and-inline-block-css-bug/<br />
**Url:** http://flipc.blogspot.sg/2009/02/damn-ie7-and-inline-block.html<br />
**Cause:** Hidden "hasLayout" property in IE.<br />
**Workaround:**<br />
```
.inline-block-example {
  display: inline-block;
  *display: inline;
  _height: 1%; /* "Holly Hack" to make this work in IE6 */
  zoom: 1;
}
```
<br /><hr />
**Issue:** Gaps between `<div>`s not due to margin or padding.<br />
**Version:** All versions<br />
**Url:** https://wordpress.org/support/topic/gap-between-div-image-slices<br />
**Cause:** Overflow<br />
**Workaround:**<br />
```
div {
  overflow: hidden;
}
```
