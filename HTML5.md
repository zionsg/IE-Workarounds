### IE workarounds for HTML5

<hr />
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
