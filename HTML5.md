### IE workarounds for HTML5

In general, issues are sorted according to the HTML5 feature in alphabetical order.
<br /><hr />
**Issue:** Sectioning elements not recognized.<br />
**Version:** IE8 and below<br />
**Url:** https://code.google.com/p/html5shim/<br />
**Url:** https://github.com/aFarkas/html5shiv<br />
**Cause:** No support<br />
**Workaround:**<br />
Download HTML5 shim or use Google CDN<br />
```
<!--[if lte IE 8]>
  <script src="//html5shim.googlecode.com/svn/trunk/html5.js"></script>
<![endif]-->
```    

<br /><hr />
**Issue:** `placeholder` attribute for `input` and `textarea` elements not supported<br />
**Version:** IE9 and below<br />
**Url:** http://mathiasbynens.be/demo/placeholder<br />
**Cause:** No support<br />
**Workaround:**<br />
Use jQuery plugin (see Url)<br />
```
<!--[if lte IE 9]>
  <script src="jquery.placeholder.min.js"></script>
  <script>
    var layoutPlaceholderScript = function() {
        $(document).ready(function() {
            $('input, textarea').placeholder();
        });
    }();
  </script>
<![endif]-->
```    
