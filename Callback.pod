TODO: Document the use of the callback along with provided data, examples, usw.

## Plugin compatibility code

Many plugins run after the page has loaded and process existing content. Since Infinite Scroll dynamically adds new content to the page, sometimes you have to execute additional code to reinitialize those plugins.

For the plugins below, the following code goes in the Javascript Callback option.

Lightbox JS 1.0:
No compatibility code available.
Lightbox JS 2.0:

`myLightbox.updateImageList();`

Shutter Reloaded:

`shutterReloaded.Init('sh');`

Thickbox:

`tb_init( $('a.thickbox, area.thickbox, input.thickbox',this) );`

1 Pixel Out Audio Player:
Compatible! Version 2.0, too.
Yahoo Media Player:

`YAHOO.MediaPlayer.addTracks( this );`

HighslideJS:

$('a.highslide',this).click(function() {  return hs.expand(this);})

WP-SimpleViewer:
Not compatible.
Flare Smith Feed Flare:
Not compatible. (relies on inline script tags)

ShareThis plugin:
Not compatible. (relies on inline script tags)

jQuery HoverIntent:

$('a.things',this).hoverIntent(......

SyntaxHighlighter Evolved:

SyntaxHighlighter.highlight(undefined,$('pre',this).get());

Smooth Scroll Links [SSL]

$('a',this).each(function(){
 ss.addEvent(this,'click',ss.smoothScroll);
});

To refer to the most recently added content:

    this;     // as of ver 1.1, the keyword this is the content wrapper (typically a DIV)
    $(this);  // the jQuery object including this
    $jQis('#infscr-page-'+INFSCR.currPage) // old 'n busted ver 1.0 style.

