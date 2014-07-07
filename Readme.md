# Infinite Scroll

<http://www.infinite-scroll.com/>

The jQuery and WordPress Plugins:

* jQuery Plugin <http://www.infinite-scroll.com/infinite-scroll-jquery-plugin/> `v2.0.2`
* WordPress Plugin <http://www.infinite-scroll.com/installation/>

##Options##
---
**debug**  
Uses `console.log` to provide info about the the plugin and as it's happening. Only intended to be  
*(Default: false)*

**prefill**  
When the document is smaller than the window, load data until the document is larger or links are exhausted  
*(Default: false)*


##Methods##
---
You can call on any Infinite Scroll method by using `$('.selector').infinitescroll('method-name');`.

**Bind**  
`$('.selector').infinitescroll('bind');`
Binds infinite scroll check on scroll to see if the plugin needs to load more content.  

**Unbind**  
Desc  

**Destroy**  
Desc  

**Pause**  
Desc  

**Resume**  
Desc  

**Toggle**  
Desc  

**Retrieve**  
Desc  

**Scroll**  
Desc  

**Update**  
Desc  


```javascript
$('.selector').infinitescroll({
  loading: {
    finished: undefined,
    finishedMsg: "<em>Congratulations, you've reached the end of the internet.</em>",
                img: null,
    msg: null,
    msgText: "<em>Loading the next set of posts...</em>",
    selector: null,
    speed: 'fast',
    start: undefined
  },
  state: {
    isDuringAjax: false,
    isInvalidPage: false,
    isDestroyed: false,
    isDone: false, // For when it goes all the way through the archive.
    isPaused: false,
    currPage: 1
  },
  behavior: undefined,
  binder: $(window), // used to cache the selector for the element that will be scrolling
  nextSelector: "div.navigation a:first",
  navSelector: "div.navigation",
  contentSelector: null, // rename to pageFragment
  extraScrollPx: 150,
  itemSelector: "div.post",
  animate: false,
  pathParse: undefined,
  dataType: 'html',
  appendCallback: true,
  bufferPx: 40,
  errorCallback: function () { },
  infid: 0, //Instance ID
  pixelsFromNavToBottom: undefined,
  path: undefined, // Can either be an array of URL parts (e.g. ["/page/", "/"]) or a function that accepts the page number and returns a URL
  maxPage:undefined // to manually control maximum page (when maxPage is undefined, maximum page limitation is not work)
});
```

In addition, you can pause infinite scroll to stop it from triggering, and later resume it.

```javascript
$('.selector').infinitescroll('pause');
$('.selector').infinitescroll('resume');
```

## Examples

### Scrolling inside an element

To scroll inside an element having `overflow`, use the `local` behavior.

```javascript
$('.selector').infinitescroll({
  behavior: 'local',
  binder: $('.selector'), // scroll on this element rather than on the window
  // other options
});
```

### Loading JSON data

As explained on the website, Infinite Scroll is designed for progressive enhancement, using existing pagination links. However, it is still possible to work with JSON data.

It means the `nextSelector` href will be called via AJAX, expecting JSON data, which will be passed to the callback function.

```javascript
$('.selector').infinitescroll({
  // other options
  dataType: 'json',
  appendCallback: false
}, function(json, opts) {
  // Get current page
  var page = opts.state.currPage;
  // Do something with JSON data, create DOM elements, etc ..
});
```

## License

The MIT License (MIT)

Copyright (c) 2014 Paul Irish

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
