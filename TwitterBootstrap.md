### IE workarounds for Twitter Bootstrap (as of v2.2.2)

In general, issues are sorted in alphabetical order, with non-working CSS classes placed first.
<br /><hr />
**Issue:** `.hidden-desktop`, `.visible-tablet`, `.visible-phone` do not work.<br />
**Version:** IE7 and below<br />
**Url:** https://github.com/twitter/bootstrap/issues/3201<br />
**Cause:** IE7 does not support `inherit` property in CSS<br />
**Workaround:**
```
<!--[if lte IE 7]>
  <style>
    .hidden-desktop-ie7 { *display: inline !important; zoom: 1; }
    .visible-tablet-ie7 { *display: inline !important; zoom: 1; }
    .visible-phone-ie7 { *display: inline !important; zoom: 1; }
  </style>
  <script>
    // IE7 hack for Twitter Bootstrap responsive utility classes as IE7 does not support 'inherit' in CSS
    var layoutInheritScript = function() {
        $(window).load(function() { ie7InheritFix(); });
        $(window).resize(function() { ie7InheritFix(); });

        function ie7InheritFix()
        {
            var windowWidth = $(window).width();
            var tabletWidth = 979; // upper range according to Twitter Bootstrap
            var phoneWidth = 767;

            $('.hidden-desktop').toggleClass('hidden-desktop-ie7', (windowWidth <= tabletWidth));
            $('.visible-tablet').toggleClass(
                'visible-tablet-ie7',
                (windowWidth <= tabletWidth) && (windowWidth > phoneWidth)
            );
            $('.visible-phone').toggleClass('visible-phone-ie7', (windowWidth <= phoneWidth));
        }
    }();
  </script>
<![endif]-->
```


<br /><hr />
**Issue:** `.span*` do not work.<br />
**Version:** IE7 and below<br />
**Url:** https://github.com/twitter/bootstrap/issues/4329<br />
**Cause:** IE7 sees a HTML comment as a first-child or at least doesn't function when a HTML comment is in front of it.<br />
**Example:**<br />
`.span9` goes below `.span3` instead of beside `.span3`
```
<div class ="row-fluid">
<!-- footer columns -- >
<div class="span3"></div>
<div class="span9"></div>
```
**Workaround:** Removing the HTML comment makes sure the first-child rule is applied properly and doesn't break your layout.


<br /><hr />
**Issue:** Dropdown items in `.navbar` do not show up in tablet/phone mode.<br />
**Version:** IE7 and below<br />
**Url:** http://brenelz.com/blog/squish-the-internet-explorer-z-index-bug/<br />
**Url:** http://dustinbrewer.com/how-to-fix-z-index-stacking-in-internet-explorer/<br />
**Cause:** IE z-index stacking bug.<br />
**Workaround:**<br />
Set a high z-index on `.navbar` in your custom CSS
```
.navbar { *z-index: 2000; }
```


<br /><hr />
**Issue:** Dropdown toggle out of alignment.<br />
**Version:** IE6<br />
**Workaround:**<br />
Add the following in your custom CSS.
```
.dropdown .dropdown-toggle { _top: 0; }
```


<br /><hr />
**Issue:** Slideshow image for jQuery AD Gallery plugin does not show.<br />
**Version:** IE9 and below<br />
**Url:** http://stackoverflow.com/questions/13179679/how-to-override-css-img-properties<br />
**Url:** http://msdn.microsoft.com/en-us/library/ms537512(VS.85).aspx#dlrevealed<br />
**Cause:** `width:auto\9` and `height:auto` in `img` rule in Bootstrap CSS.<br />
**Workaround:**<br />
The CSS workaround mentioned in the _Stackoverflow_ answer will not work for IE7 as it does not support the `inherit` property.<br />
To support IE7 onwards, remove the conflicting CSS rules from the Bootstrap CSS, save as another file.<br />
Load the Bootstrap CSS for non-IE browsers using downlevel-revealed conditional comments and
load the modified file with downlevel-hidden conditional comments.
```
<![if !IE]><link href="bootstrap.min.css" media="screen" rel="stylesheet" type="text/css"><![endif]>
<!--[if IE]><link href="bootstrap-ie-workaround.min.css" media="screen" rel="stylesheet" type="text/css"><![endif]-->
```
