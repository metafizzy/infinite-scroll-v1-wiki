##  loading
####  finished
####  finishedMsg
####  img
####  msg
####  msgText
####  selector
####  speed
####  start

##  state
####  isDuringAjax
####  isInvalidPage
####  isDestroyed
####  isDone
####  isPaused
####  <a id="currPage"></a>currPage

## Regular Options
####  debug
`boolean`

Default: `false`

Displays debugging information related to the operations of the plugin.

####  behavior

####  binder

####  <a id="nextSelector"></a>nextSelector

####  navSelector

####  contentSelector

####  extraScrollPx

####  itemSelector
`string`

Default: `"div.post"`

The `itemSelector` is used to find the HTML elements that are inserted into the page when the [`dataType`](#dataType) option is set to `"html"`.

####  animate
`boolean`

Default: `true`

Determines whether or not to animate scrolling after new elements have been appended to the DOM.

####  pathParse

####  <a id="dataType"></a>dataType
`string`

Default: `"html"`

Determines the expected return type of any AJAX calls made by the plugin. Possible values include `"html"` and `"json"`. The `"json"` option should be used in conjunction by setting the [appendCallback](#appendCallback) to false and using the [append callback](Callback) to generate your page structure from the returned JSON.

####  <a id="appendCallback"></a>appendCallback

####  bufferPx

####  errorCallback
`function`

Default: `function() { }`

Function that is called at the end of Infinite-Scroll's execution. Takes in a string with the value `"done"` as an argument. This appears to be a vestigial option with no real use and may be removed in the future. It's use is not recommended.

####  infid

####  pixelsFromNavToBottom

####  <a id="path"></a>path
`object` (array) or `function`

Default: `undefined`

When set to either a string or a function, this will override Infinite Scroll's default attempt to guess the format of the URL pulled from the `href` of the element found by the [nextSelector](#nextSelector). 

When an array is supplied, it should be broken down in a manner such that it will return a `string` representative of the URL to the next page when `.join(currentPageNumber)` is called on it.

    ["/path/to/resource/page/", "/html"]

If a function is passed in to `path`, the function will take one argument, `currentPageNumber`, which is a `number`. The function should return a URL as a `string` that will be used to fetch the next page.

    function generatePageUrl(currentPageNumber) { return ("/path/to/resource/page/" + currentPageNumber + "/html"); }

####  prefill
`boolean`

Default: `false`

When set to true, Infinite Scroll will continue to load more pages until the window is full enough to trigger the vertical scrollbar. If the window is resized to be large enough to hide the vertical scrollbar, Infinite Scroll will load more content until the window is full again.

####  maxPage
`number`

Default: `undefined`

This option is used to limit the number of pages that will be loaded by Infinite Scroll. Pages will continue loading until the page, as indicated by the [current page state variable](#currPage), exceeds the value of `maxPage`.