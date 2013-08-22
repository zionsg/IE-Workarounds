### IE workarounds for CSS

In general, issues are sorted according to the CSS property in alphabetical order.
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
