## Infinite Scroll jQuery Plugin

Note: This documentation is currently out-of-date and will be updated soon. In the mean time, please refer to the GitHub [README](https://github.com/paulirish/infinite-scroll/blob/master/Readme.md) and [Wiki](https://github.com/paulirish/infinite-scroll/wiki/_pages).

This plugin aims to progressively enhance your page. Your navigation/pagination elements should be present in the HTML for non-js users, but the plugin will utilize those links to build out a more rich browsing experience.

#### Download the jQuery plugin

Version 1.5.100504

[jquery.infinitescroll.js and minified are now on GitHub](https://github.com/paulirish/infinite-scroll)

#### Usage
Minimum required configuration

This is the minimum amount of configuration you can do, if you want things to work:

```js
// infinitescroll() is called on the element that surrounds 
// the items you will be loading more of
  $('#content').infinitescroll({
 
    navSelector  : "div.navigation",            
                   // selector for the paged navigation (it will be hidden)
    nextSelector : "div.navigation a:first",    
                   // selector for the NEXT link (to page 2)
    itemSelector : "#content div.post"          
                   // selector for all items you'll retrieve
  });
```

All options

```js
// usage:
// $(elem).infinitescroll(options,[callback]);
 
// infinitescroll() is called on the element that surrounds 
// the items you will be loading more of
$('#content').infinitescroll({
 
  navSelector  : "div.navigation",            
                 // selector for the paged navigation (it will be hidden)
 
  nextSelector : "div.navigation a:first",    
                 // selector for the NEXT link (to page 2)
 
  itemSelector : "#content div.post",          
                 // selector for all items you'll retrieve
 
  debug        : true,                        
                 // enable debug messaging ( to console.log )
 
  loadingImg   : "/img/loading.gif",          
                 // loading image.
                 // default: "http://www.infinite-scroll.com/loading.gif"
 
  loadingText  : "Loading new posts...",      
                 // text accompanying loading image
                 // default: "<em>Loading the next set of posts...</em>"
 
  animate      : true,      
                 // boolean, if the page will do an animated scroll when new content loads
                 // default: false
 
  extraScrollPx: 50,      
                 // number of additonal pixels that the page will scroll 
                 // (in addition to the height of the loading div)
                 // animate must be true for this to matter
                 // default: 150
 
  donetext     : "I think we've hit the end, Jim" ,
                 // text displayed when all items have been retrieved
                 // default: "<em>Congratulations, you've reached the end of the internet.</em>"
 
  bufferPx     : 40,
                 // increase this number if you want infscroll to fire quicker
                 // (a high number means a user will not see the loading message)
                 // new in 1.2
                 // default: 40
 
  errorCallback: function(){},
                 // called when a requested page 404's or when there is no more content
                 // new in 1.2                   
 
  localMode    : true
                 // enable an overflow:auto box to have the same functionality
                 // demo: http://paulirish.com/demo/infscr
                 // instead of watching the entire window scrolling the element this plugin
                 //   was called on will be watched
                 // new in 1.2
                 // default: false
 
    },function(arrayOfNewElems){
 
     // optional callback when new content is successfully loaded in.
 
     // keyword `this` will refer to the new DOM content that was just added.
     // as of 1.5, `this` matches the element you called the plugin on (e.g. #content)
     //                   all the new elements that were found are passed in as an array
 
});
```
#### Custom trigger, non-automatic. Twitter-style

In 1.4 you can trigger the loading of the next page of content at will. You’ll first unbind the default behavior. And then trigger the next pull whenever you like..
```
// unbind normal behavior. needs to occur after normal infinite scroll setup.
$(window).unbind('.infscr');
```
```
// call this whenever you want to retrieve the next page of content
// likely this would go in a click handler of some sort
$(document).trigger('retrieve.infscr');
```
[Demo of the triggered infinite scroll functionality.](http://www.infinite-scroll.com/trigger.html)

#### How does it work?

There is a little known feature in the .load() method that lets you specify the CSS selector of the html you want to include. jQuery will load in any local URL, then parse the html and grab only the elements you’ve defined with your selector. This allows for some pretty fun shit: client-side transclusions (a la [purple include](http://ajaxian.com/archives/purple-include-transclusions-you-know-you-want-them)) ; and some really kickass shit when you combo it with a [local php proxy](http://developer.yahoo.com/javascript/howto-proxy.html).

This is really the meat of the code:
```
// load all post divs from page 2 into an off-DOM div
$('
```
```
').load('/page/2/ #content div.post',function(){ 
    $(this).appendTo('#content');    // once they're loaded, append them to our content area
});
```
So it basically leverages that load() method at its core. It’s basically scraping your existing page structure, which means you don’t need to code any custom backend stuff to enable this functionality! Booyah, right?


## WordPress Plugin Installation

* [Download the plugin](downloads.wordpress.org/plugin/infinite-scroll.zip).
* Install it to your /wp-content/plugins/ directory
* Activate the plugin in your WordPress Admin UI.
* Visit the Settings / Infinite Scroll page to set up the css selectors.
* The plugin will now work for a logged in Admin, but will be disabled for all other users; you can change this.

#### CSS Selector Setup

You need configure the plugin with CSS selectors that match your theme.

![selector](http://www.infinite-scroll.com/wp-content/uploads/2008/06/selectors2.jpg)

 *  Content CSS Selector  
The DIV that wraps around all posts. New posts will be inserted at the bottom of this DIV. 
 *  Post CSS Selector      
The selector that selects all posts on a page. Each post must be surrounded by a single DIV. 
 *  Navigation links CSS Selector      
This DIV contains the Next Posts and Previous Posts link. 
 *  Previous Posts CSS Selector      
This A tag is what points to the 2nd page of posts. 

#### Troubleshooting

* Your posts need to be wrapped in divs all next to each other.
* You need a link on your page to the next page of posts.

#### FAQ

-Can I change the number of posts loaded?  
    Yup. But that’s a WordPress thing. Go to Settings / Reading  
-Is it SEO-Friendly?  
    Yes all enhancements are made via javascript only, so search spiders see no difference.  
-Is it accessible?  
    Things won’t change for screen-readers. This technique degrades gracefully.  
-Why doesn’t it work on ____ page?  
    Currently, the plugin is disabled for everything but the main page, but I’ll work on enabling it for Archives, Categories, and Tags.  
-Does it still keep going, even at the end of the blog?  
    Infinite scroll is configured to die when it hits a 404 Not Found status code, so when it goes through all your archives it should hit a /page/43/ (or something) that doesn’t exist, then show a message “Congrats, you’ve reached the end of the internet.” Some wordpress themes don’t report not found pages with a 404. Try a different theme or contacting the theme author.  
-Do I need to edit my theme to make this work?  
    Probably not, nope.  
-Will this do form posts for get new data?  
    Nope?  
-You mean it just works?  
    Yup.  
-Really?  
    I hope so. But due to the infinitudes of wordpress installations, each case is different. Different themes and other plugins may break infinite scroll’s functionality.  

#### Customization

This information will probably help styling.

* `<div id="infscr-page-2" class="infscr-pages">` will contain the page 2 content, etc
* `<div id="infscr-loading">` is the loading div.

