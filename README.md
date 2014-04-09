# jQuery Scrollfire

Version 1.4.0

## Summary

Allows useful callbacks to be fired upon elements scrolling into and out of view from both the top and bottom of the viewport/window. Additionally, provides a mechanism to animate parallax elements.

## Author

Wil Neeley ( [@wilneeley](http://twitter.com/wilneeley) / [trestlemedia.net](http://www.trestlemedia.net) / [github.com](https://github.com/Xaxis) )

## Overview

jQuery.scrollfire gives its users the ability to execute callbacks on a multitude of scroll based events.
* ... implement way points to trigger menu animations.
* ... easily animate elements with parallax effects.
* ... add infinite scrolling via ajax to load content at set scroll positions.
* ... call functions when elements scroll into and/or out of view.
* ... call functions when elements scroll COMPLETELY into/out of view.
* ... call functions based on scroll direction ONLY when an element is in view.
* ... call functions based on scroll direction continuously.
* ... call functions at any scroll position.

## Usage

Include `jquery.scrollfire.min.js` after jQuery.

### Initializing Scrollfire

```javascript
// Example of initializing scrollfire with all of its callbacks and most of its properties
$('.container').scrollfire({

    // Offsets
    offset: 0,
    topOffset: 150,
    bottomOffset: 150,

    // Fires once when element begins to come in from the top
    onTopIn: function( elm, distance_scrolled ) {
        $(elm).animate({opacity: 1.0}, 500);
        $(elm).removeClass('fully-visible');
        $(elm).find('.parallax-cell').html('onTopIn');
    },

    // Fires once when element beings to go out at the top
    onTopOut: function( elm, distance_scrolled ) {
        $(elm).animate({opacity: 0.2}, 500);
        $(elm).removeClass('fully-visible');
        $(elm).find('.parallax-cell').html('onTopOut');
    },

    // Fires once when element begins to come in from the bottom
    onBottomIn: function( elm, distance_scrolled ) {
        $(elm).animate({opacity: 1}, 500);
        $(elm).removeClass('fully-visible');
        $(elm).find('.parallax-cell').html('onBottomIn');
    },

    // Fires once when element begins to go out at the bottom
    onBottomOut: function( elm, distance_scrolled ) {
        $(elm).animate({opacity: 0.2}, 500);
        $(elm).removeClass('fully-visible');
        $(elm).find('.parallax-cell').html('onBottomOut');
    },

    // Fires once when element goes completely out of view at the top
    onTopHidden: function( elm ) {
        $(elm).removeClass('fully-visible').addClass('fully-hidden');
        $(elm).find('.parallax-cell').html('onTopHidden');
    },

    // Fires once when element completely comes into view from the bottom
    onBottomVisible: function( elm ) {
        $(elm).removeClass('fully-hidden').addClass('fully-visible');
        $(elm).find('.parallax-cell').html('onBottomVisible');
    },

    // Fires once when element goes completely out of view at the bottom
    onBottomHidden: function( elm ) {
        $(elm).removeClass('fully-visible').addClass('fully-hidden');
        $(elm).find('.parallax-cell').html('onBottomHidden');
    },

    // Fires once when element completely comes into view from the top
    onTopVisible: function( elm ) {
        $(elm).removeClass('fully-hidden').addClass('fully-visible');
        $(elm).find('.parallax-cell').html('onTopVisible');
    },

    // Fires continuously while scrolling in either direction while element is in at least partial view
    onScroll: function( elm, distance_scrolled ) {
    },

    // Fires continuously while scrolling down and while the element is in at least partial view
    onScrollDown: function( elm, distance_scrolled ) {
    },

    // Fires continuously while scrolling up and while the element is in at least partial view
    onScrollUp: function( elm, distance_scrolled ) {
    },

    // Fires continuously while scrolling in either direction regardless of if the element is in view
    onScrollAlways: function( elm, distance_scrolled ) {
    },

    // Fires continuously while scrolling down regardless of if the element is in view
    onScrollDownAlways: function( elm, distance_scrolled ) {
    },

    // Fires continuously while scrolling up regardless of if the element is in view
    onScrollUpAlways: function( elm, distance_scrolled ) {
    }
});
```

```javascript
// Example of parallaxing an element within its parent container (default behavior)
$('.parallax-cell-1').scrollfire({
    parallax: {
        active: true,
        parent: $('.parallax-cell-1').parent()
    }
});


// Example of using parallaxed element that respects its margins as a boundary
$('.parallax-cell-2').scrollfire({
    parallax: {
        active: true,
        bound: true,
        speed: 150,
        easing: 'linear'
    }
});


// Example of inverting a parallax element's direction
$('.parallax-cell-3').scrollfire({
    parallax: {
        active: true,
        bound: false,
        invert: true,
        speed: 150,
        easing: 'linear'
    }
});


// Example of adjusting the parallax speed and easing
$('.parallax-cell-4').scrollfire({
    parallax: {
        active: true,
        bound: false,
        invert: false,
        speed: 500,
        easing: 'swing'
    }
});


// Example of adjusting the parallax distance by a scalar multiplier
$('.parallax-cell-5').scrollfire({
    parallax: {
        active: true,
        bound: false,
        invert: false,
        speed: 10,
        easing: 'linear',
        scalar: 0.25
    }
});


// Parallax multiple elements (active is the only required property)
$('.parallax-cell-6, .parallax-cell-7, .parallax-cell-8, .parallax-cell-9').scrollfire({
    parallax: {
        active: true
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

#### Version 1.2.0

* added immediate parallax initialization

#### Version 1.3.0

* added parallax bounding functionality

#### Version 1.4.0

* refined scrollfire methods
* added parallax speed, easing, invert, scalar, and active properties