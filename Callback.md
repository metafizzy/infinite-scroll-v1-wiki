######TODO: Document the use of the callback along with provided data, examples, usw.

## Plugin compatibility code

Many plugins run after the page has loaded and process existing content. Since Infinite Scroll dynamically adds new content to the page, sometimes you have to execute additional code to reinitialize those plugins.

For the plugins below, the following code goes in the Javascript Callback option.

####[Lightbox JS 1.0:](http://lokeshdhakar.com/projects/lightbox/)
No compatibility code available.

####[Lightbox JS 2.0:](http://lokeshdhakar.com/projects/lightbox2/)

    myLightbox.updateImageList();

####[Shutter Reloaded:](http://www.laptoptips.ca/projects/wp-shutter-reloaded/)

    shutterReloaded.Init('sh');

####[Thickbox:](http://jquery.com/demo/thickbox/)

    tb_init( $('a.thickbox, area.thickbox, input.thickbox',this) );

####[1 Pixel Out Audio Player:](http://www.1pixelout.net/code/audio-player-wordpress-plugin/)
Compatible! Version 2.0, too.

####[Yahoo Media Player:](http://webplayer.yahoo.com/)

    YAHOO.MediaPlayer.addTracks( this );

####[HighslideJS:](http://highslide.com/)

    $('a.highslide',this).click(function() {  return hs.expand(this);})

####[WP-SimpleViewer:](http://www.simpleviewer.net/simpleviewer/support/wp-simpleviewer/)
Not compatible.

####[Flare Smith Feed Flare:](http://xentek.net/code/wordpress/plugins/flaresmith/)
Not compatible. (relies on inline script tags)

####ShareThis plugin:
Not compatible. (relies on inline script tags)

####jQuery HoverIntent:

    $('a.things',this).hoverIntent(......

####[SyntaxHighlighter Evolved:](http://wordpress.org/extend/plugins/syntaxhighlighter/)

    SyntaxHighlighter.highlight(undefined,$('pre',this).get());

####Smooth Scroll Links [SSL]
```
$('a',this).each(function(){
 ss.addEvent(this,'click',ss.smoothScroll);
});
```
####To refer to the most recently added content:
```
    this;     // as of ver 1.1, the keyword this is the content wrapper (typically a DIV)
    $(this);  // the jQuery object including this
    $jQis('#infscr-page-'+INFSCR.currPage) // old 'n busted ver 1.0 style.
```
