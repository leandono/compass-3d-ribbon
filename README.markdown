#3D CSS Ribbons

An extension (for [Compass](http://compass-style.org/)) to create 3D ribbons using only CSS. 
**[Live example](http://codepen.io/dzignus/pen/yjLwD)**.

![some nice example](http://i.imgur.com/O7o32NZ.png)

The extension is inspired in [3D Ribbon Generator](http://www.css3d.net/ribbon-generator/).


#Installation

From the command line:

    sudo gem install 3d-ribbon

Installing into an existing project:

    # edit the project configuration file and add:
    require '3d-ribbon'

	#from the command line
    compass install 3d-ribbon

	#import the extension into your scss/sass file
	@import "3d-ribbon"

If you don't have/want use Compass, you can [download the main sass](https://github.com/dzignus/compass-3d-ribbon/blob/master/stylesheets/_3d-ribbon.scss) file and import it:

```scss
@import "<path to the file>/_3d-ribbon.scss"
```

#Intro

The extension offer a simple and flexible way to create 3D ribbons with CSS.

Browser support:

* IE8+
* Firefox
* Google Chrome
* Safari / Safari iOS

## First, in your HTML document:

You only need a block element to apply the ribbon, for example:

	<h3 class="ribbon">This is my title</h3>

## Then, in your Sass document:

**The simple way**:

```scss
.ribbon{
  @include ribbon();
}
```

**The flexible way (with all options)**:

```scss
.ribbon{
    @include ribbon(
        // Set the background color of the ribbon
        $background-color    : <color>,

        // Set the position of the sides
        $position            : <bottom> | <top>,

        // Set the sides of the ribbon
        $sides               : <left> | <rigth> | <left right>,

        // Set the width of the overlaps
        $overlap-horizontal  : <width>,

        // Set the height of the overlaps
        $overlap-vertical    : <height>,

        // Set the color of the edges
        $overlap-color       : <color>
    )
}
```

#Settings:

## $background-color: 

Set the background color of the ribbon. Default value: `#428bca`.


## $position:

Set the position of the sides. Default value: `top`.


## $sides:

Set the sides of the ribbon. Default value: `left right`.


## $overlap-horizontal:

Set the width of the overlaps. Default value: `30px`.


## $overlap-vertical:

Set the height of the overlaps. Default value: `20px`.


## $overlap-color:

Set the color of the edges. Default value: `darken(#428bca, 30%)`.


#Adding the ribbon's back

If you want the ribbon's back you need add some spans into your HTML:

```scss
<h3 class="ribbon">
	This is my title
	<span class="ribbon-left"></span>
	<span class="ribbon-right"></span>
</h3>
```

Later in your sass use the `ribbon-back` mixin:

```scss
.ribbon-left{
  @include ribbon-back($side: left);
}

.ribbon-right{
  @include ribbon-back($side: right);
}
```

The mixin also have many setting for customization:

```scss
.ribbon-back{
    @include ribbon-back(
        // The side to create. This is the only required param
        $side,

        // Set the background color of the ribbon's back
        $background-color    : <color>,

        // Set the position of the ribbon's back
        $position            : <top> | <bottom>,

        // Set the height of the ribbon's back
        $height              : <height>,

        // Set the width of the ribbon's back
        $width               : <width>,

        // Set the vertical distance of the ribbon's back
        $horizontal-distance : <height>,

        // Set the horizontal distance of the ribbon's back
        $vertical-distance   : <width>,

        // Set the color of the back's snip
        $snip-color          : <color>
    )
}
```

It's probably that the two mixins (`ribbon` and `ribbon-back`) share values, so, the best way is declare some variables to use with the mixins. For example:

```scss
$ribbon-background-color: #d9534f;
$ribbon-position: top;
$ribbon-sides: left right;
$ribbon-overlap-horizontal-distance: 20px;
$ribbon-overlap-vertical-distance: 15px;
$ribbon-back-width: 20px;
$ribbon-back-height: 30px;

.ribbon{
  @include ribbon(
    $background-color: $ribbon-background-color,
    $position: $ribbon-position,
    $sides: $ribbon-sides,
    $overlap-horizontal: $ribbon-overlap-horizontal-distance,
    $overlap-vertical: $ribbon-overlap-vertical-distance,
    $overlap-color: darken($ribbon-background-color, 30%) 
   );

  @each $side in $ribbon-sides {

    .ribbon-#{$side}{
      @include ribbon-back(
      $side: #{$side},
      $background-color: $ribbon-background-color,
      $position: $ribbon-position,
      $width: $ribbon-back-width,
      $height: $ribbon-back-height,
      $horizontal-distance: $ribbon-overlap-horizontal-distance,
      $vertical-distance: $ribbon-overlap-vertical-distance,
      $snip-color: transparent
      );
    }

  }
  
}
```

**[Live example](http://codepen.io/dzignus/pen/yjLwD)**