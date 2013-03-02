##The History of Infinite Scroll

Here is the history as far as I’ve seen it:

* 2005 June 23 – [Ma.La releases the Google Auto Pager greasemonkey script.](http://la.ma.la/blog/diary_200506231749.htm)
* 2005 June 28 – Bill Scott releases Rico LiveGrid and writes [“Death To Paging!”](http://looksgoodworkswell.blogspot.com.ar/2005/06/death-to-paging-rico-livegrid-released.html)
* 2006 April 25 – [Humanized Reader launches with “Infinite History”](http://humanized.com/weblog/2006/04/25/no_more_more_pages/)
* 2006 September 14(ish) – Yahoo Mail (beta) utilizes the same LiveGrid technology
* 2006 September 17 – Microsoft’s [Live.com Image Search includes infinite scroll.](http://ajaxian.com/archives/ms-livecom-ajax-image-search)
* 2006 October 31 – Peter Forde writes [Endless Pageless](http://unspace.ca/archive/) and releases a Rails plugin
* 2007 April 17 – [swdyh releases AutoPagerize greasemonkey script,](http://userscripts.org/scripts/show/8551) enabling infinite scroll for nearly every site.
* 2008 June 29 – infinite-scroll.com debuts with initial release of wordpress plugin

(*) Google Reader uses the same preloading LiveGrid technology. Anyone know when this debuted?

##Changelog

* 2008 June 29 – 1.0 release.
* 2008 September 25 – 1.1 release.
 * Rewritten as a jQuery plugin.
 * Added animation.
* 2009 August 4th – 1.2 release.
 * More robust URL path regex.
 * getoption(‘siteurl’) fix made.
 * jQuery plugin version updated. many more options available.
 * Release backwards compatible
* 2009 September 15th – 1.3 release.
 * Fix from cosmin on loadingText key name.
 * Use enqueue_script() and plugins_url
* 2009 November 29th – 1.4 release.
 * Reverting enqueue_script() change. It breaks on all sorts of themes and situations
 * Custom events model. Allows for triggering on a click, a la twitter style.
* 2010 February 10th – 1.4.100210 release.
 * Fixing a small bug that jQuery 1.4 introduced.
* 2010 May 4th – 1.5.100504 release.
 * Success callback receives `this` context value now (it matches whatever plugin was called on)
 * Callback also receives array of new elements as first arg
 * Drupal URL support (thanks Jerod and Vladikoff)
 * [Code moved to Github](https://github.com/paulirish/infinite-scroll)
