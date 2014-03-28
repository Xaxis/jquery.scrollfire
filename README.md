# jQuery Scrollfire

Version 1.2.0

## Summary

Allows useful callbacks to be fired upon elements scrolling into and out of view from both the top and bottom of the viewport/window. Additionally, provides a mechanism to animate parallax elements.

## Author

Wil Neeley ( [@wilneeley](http://twitter.com/wilneeley) / [trestlemedia.net](http://www.trestlemedia.net) / [github.com](https://github.com/Xaxis) )

## Overview

jQuery.scrollfire gives its users the ability to execute callbacks on a multitude of scroll based events.
* ... easily animate elements with parallax effects.
* ... add infinite scrolling via ajax to load content at set scroll positions.
* ... call functions when an element(s) scrolls into and/or out of view (firing on the top or bottom of the element).
* ... call functions based on scroll direction ONLY when an element is in view.
* ... call functions based on scroll direction continuously.
* ... fire code at any scroll position via the usage of element targeting in combination with specifying an offset.

## Usage

Include `jquery.scrollfire.min.js` after jQuery.

## Detailed Summary

Often it is useful to have the ability to execute code upon the scrolling of an element(s) into and/or out of view. jQuery.scrollfire gives you this ability via four callback methods: `onTopIn`, `onTopOut`, `onBottomIn`, and `onBottomOut`.

### Initializing Scrollfire

```javascript
// Example of initializing scrollfire with all of its callbacks and most of its properties
$('.container').scrollfire({
    offset: 100,
    //topInOffset: 0,
    //topOutOffset: 0,
    //bottomInOffset: 0,
    //bottomOutOffset: 0,
    onTopIn: function( elm, distance_scrolled ) {
        $(elm).animate({opacity: 1}, 500);
    },
    onTopOut: function( elm, distance_scrolled ) {
        $(elm).animate({opacity: 0.2}, 500);
    },
    onBottomIn: function( elm, distance_scrolled ) {
        $(elm).animate({opacity: 1}, 500);
    },
    onBottomOut: function( elm, distance_scrolled ) {
        $(elm).animate({opacity: 0.2}, 500);
    },
    onScroll: function( elm, distance_scrolled, scroll_direction ) {
        //console.log('Happening continuously while scrolling in either direction');
    },
    onScrollDown: function( elm, distance_scrolled, percentage_to_top ) {
        //console.log('Continuously happening while scrolling down when element is in view!');
    },
    onScrollUp: function( elm, distance_scrolled, percentage_to_top ) {
        //console.log('Continuously happening while scrolling up when element is in view!');
    },
    onScrollDownAlways: function( elm, distance_scrolled ) {
        //console.log('Continuously happening while scrolling down!');
    },
    onScrollUpAlways: function( elm, distance_scrolled ) {
        //console.log('Continuously happening while scrolling up');
    }
});


// Example of using parallax scrolling
$('.parallax-cell').scrollfire({

    // Parallax active when element is outside of offset
    offset: 100,
    parallax: {

        // The element the jQuery selected element is a direct child of
        childOf: $('.container'),

        // Parallax is 75% the window scrolling speed
        speed: 0.75
    },

    // Additionally, you can still use any of the callbacks
    onScroll: function( elm, distance_scrolled, direction ) {
        //console.log('Happening continuously!');
    }
});
```

### Using Scrollfire Methods

```javascript
// Remove an element(s) from scrollfire.
$('.parallax-cell').scrollfire('remove');
```

### Caveats

None reported/observed. Have fun.

## Requirements/Browsers

Tested with jQuery 1.4.x.

Works in IE6+, Chrome 14+, Safari 4+, Firefox 3.0+, Opera 10+.

## Examples

See `example.html` in examples folder.

### Changelog

#### Version 1.0.0

* initial version

#### Version 1.1.0

* added parallax scrolling methods: `onScrollDown`, `onScrollUp`, and `onScroll`

### Version 1.2.0

* added immediate parallax initialization