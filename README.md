# jQuery Scrollfire

Version 1.1.0

## Summary

Allows useful callbacks to be fired upon elements scrolling into and out of view from both the top and bottom of the viewport/window. Additionally, provides a mechanism to animate parallax elements.

## Author

Wil Neeley ( [@wilneeley](http://twitter.com/wilneeley) / [trestlemedia.net](http://www.trestlemedia.net) / [github.com](https://github.com/Xaxis) )

## Usage

Include `jquery.scrollfire.min.js` after jQuery.

## Detailed Summary

Often it is useful to have the ability to execute code upon the scrolling of an element(s) into and/or out of view. jQuery.scrollfire gives you this ability via four callback methods: `onTopIn`, `onTopOut`, `onBottomIn`, and `onBottomOut`.

### Register Scrollfire on Elements

```javascript
// Example attached to DIVs with class .container
$('.container').scrollfire({
    //offset: 200,              // Default offset setting
    //topInOffset: 0,           // Further offset properties override the default offset setting
    //topOutOffset: 0,          // ...
    //bottomInOffset: 0,        // ...
    //bottomOutOffset: 0,       // ...
    onTopIn: function( elm ) {
        $(elm).animate({width: "100%"}, 500, function() {
            $(this).css('border', '2px dashed deeppink');
        });
    },
    onTopOut: function( elm ) {
        $(elm).animate({width: "100px"}, 500, function() {
            $(this).css('border', '2px dashed deeppink');
        });
    },
    onBottomIn: function( elm ) {
        $(elm).animate({width: "100%"}, 500, function() {
            $(this).css('border', '2px solid black');
        });
    },
    onBottomOut: function( elm ) {
        $(elm).animate({width: "100px"}, 500, function() {
            $(this).css('border', '2px solid black');
        });
    },
    onScrollDown: function( elm, distance_scrolled, percentage_to_top ) {
      var div = $(elm);
      var div_height = div.height();
      var parallax_pos = (div_height * from_top) - $('.parallax-cell').outerHeight();
      $(elm).find('.parallax-cell').css('top', parallax_pos);
    },
    onScrollUp: function( elm, distance_scrolled, percentage_to_top ) {
      var div = $(elm);
      var div_height = div.height();
      var parallax_pos = (div_height * from_top) - $('.parallax-cell').outerHeight();
      $(elm).find('.parallax-cell').css('top', parallax_pos);
    },
    onScroll: function( elm, distance_scrolled, scroll_direction ) {
      //console.log('Happening continuously);
    }
});
```

### Using Scrollfire Methods

```javascript
// Remove an element(s) from scrollfire.
$('.cell').scrollfire('remove');
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