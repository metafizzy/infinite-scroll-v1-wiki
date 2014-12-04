[View Wiki Table of Contents](https://github.com/paulirish/infinite-scroll/wiki/_pages)

## The Interaction Design Pattern
Infinite scroll has been called autopagerize, unpaginate, endless pages. But essentially it is pre-fetching content from a subsequent page and adding it directly to the user’s current page.

### Problem Summary
User is browsing paged content.

### Use When
* Retaining the user is important and clicking “Next Page” is a usability barrier.
* The full content available is too large to show on initial load.
* The content is available in paged chunks: search results, blog posts, product listings portfolio features.  
![InfiniteScroll Pattern](http://www.infinite-scroll.com/wp-content/uploads/2008/07/infinite-scroll-pattern.gif)

### Advantages
* Users are retained on the site far better.
** Users are less likely to continue on to the next “page” if they have to click something versus it being delivered automatically to them. [citation needed]
* Requires no adjustment in a user's typical reading habits.
* The added functionality needs no affordances or instruction.
* As long as the functionality is enhancing an existing navigational structure (like the wordpress plugin here), it remains SEO-friendly and Accessible. It will degrade gracefully if a user does not have JavaScript enabled..

### Disadvantages
* On most webpages the "footer" of the page will be typically impossible to reach.
* Currently there is no way for the user to cancel or opt-out of the behavior. *
* There is no permalink to a given state of the page. *
* Dynamically adding more content to the page increases the memory footprint of the browser. Depending on the browser, this could account for around 50 MB of RAM.
* Analytics will not immediately capture the event, so custom configuration is required.
* [FOR GOD'S SAKE, DON'T BREAK THE BACK BUTTON.](http://tumbledry.org/2011/05/12/screw_hashbangs_building). *  
  
(*) Although this could be easily implemented on an as-needed basis by calling the plugin's API.

### Implementation Recommendations
* Depending on site latency, new content can be fetched aggressively (when a user has 500px of the page left to scroll) versus at the last moment (with ~100px left).
* User should be notified when there is no more content available. 
* Consider a faux pagination widget to allow for navigation within the new content. [Travis Isaacs has ideas on a running pagination](http://travisisaacs.com/2008/02/24/improving-on-infinite-scrolling/).
* Infinite scroll should be implemented as progressive enhancement. Typical navigation/pagination should be present for users with JavaScript disabled. JavaScript-enabled users, however, will experience the more rich reading functionality.

### Examples in the Wild
* [SocialThing](http://socialthing.com/)
* [Live.com Image Search](http://search.live.com/images/results.aspx?q=scrollbar&go=&form=QBIR)
* [Soup tumblelogs](http://www.soup.io/)
* [Google Reader](http://www.google.com/reader/), [Yahoo Mail](http://mail.yahoo.com/) use the same technique but within a container.
* [Dazed Digital](http://www.dazeddigital.com/)