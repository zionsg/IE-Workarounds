### IE workarounds for AD Gallery jQuery plugin (as of v1.2.7)

Website: http://coffeescripter.com/code/ad-gallery

<br /><hr />
**Issue:** Slideshow image does not show in IE10.<br />
**Version:** IE10<br />
**Cause:** IE10 returns 0 for image.width and image.height.<br />
**Workaround:**<br />
Use image.naturalWidth and image.naturalHeight instead, but image.width and image.height must take precedence
else the slideshow will not show for the other browsers and lesser IE versions.

_This solution requires source code modification_
```
// Original source code at line 794 in jquery.ad-gallery.js
image.size = { width: this.width, height: this.height };
```

```
// Change to:
image.size = {
    width: (this.width || this.naturalWidth),
    height: (this.height || this.naturalHeight)
};
```
