#3D CSS Ribbons

A extension (for [Compass](http://compass-style.org/)) to create 3D ribbons using only CSS. 
**[Live example](http://jsfiddle.net/dzignus/LXJ7X/)**.

![some nice example](http://static.tumblr.com/djfsbl4/N1qllypq4/ribbon_example.png) 

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

Or create a new project:

    compass create <project_name> -r 3d-ribbon --using 3d-ribbon 

	#import the extension into your scss/sass file
	@import "3d-ribbon"




#Intro

The extension offer a simple and flexible way to create 3D ribbons with CSS.

Browser support:

* IE7+
* Firefox 3.5+
* Google Chrome
* Safari / Safari iOS

Note: In IE7/8, box-shadows and border-radius only using [CSS3 Pie](http://compass-style.org/reference/compass/css3/pie/).

## First, in your HTML document:

This is the basic structure to create a ribbon with two sides (left / right):

	<div id="ribbon-example-foo">

		<!--start ribbon-->
		<div class="ribbon-wrapper">
			<div class="ribbon-front">
			
				Here you can put some content (like "Lorem ipsum dolor sit amet...") or HTML elements
				
			</div>
			<div class="ribbon-edge-left-top"></div>
			<div class="ribbon-edge-right-top"></div>
			<div class="ribbon-edge-left-bottom"></div>
			<div class="ribbon-edge-right-bottom"></div>
			<div class="ribbon-back-left"></div>
			<div class="ribbon-back-right"></div>
		</div>
		<!--end ribbon -->

	</div>


If you need only one side in the ribbon, you can remove some `<div />`. For example, if you need a ribbon with only the right side, you can remove `<div class="ribbon-edge-left-top"></div>`, `<div class="ribbon-edge-left-bottom"></div>` and `<div class="ribbon-back-left"></div>`.


## Then, in your Sass document:

**The simple way**:

    #ribbon-example-foo{
      @include ribbon($front-width: 400px);
    }

**The flexible way (with all options)**:

    #ribbon-example-foo{
      @include ribbon(
              $front-width: 750px,
              $sides: left-bottom,
              $ribbon-height: 40px,
              $front-color: #80B5AD, 
              $edges-color: darken(#8ABD9A, 30%), 
              $back-color: #8DBF96,
              $back-width: 30px, 
              $overlap-width: 35px, 
              $overlap-height: 15px,
              $border-radius: 7px,
              $include-pie: true);
    }



#Settings:

## $front-width: 

The width of the ribbon content, in px. This is the only mandatory argument.


## $sides:

The sides of the ribbon (left / right) and position (top / bottom). Options availables:

* `left-top`
* `left-bottom`
* `right-top`
* `right-bottom`

For example, is you want a ribbon with only one side (right) and orientation top:

      @include ribbon($front-width: 450px, $sides: right-top);


Default value: `left-bottom right-bottom`.


## $ribbon-height:

The height of the ribbon, in px. Default value: `40px`.


## $front-color:

The color of the front of the ribbon. Default value: `#3A89CE`.


## $edges-color:

The color of the edges of the ribbon. Default value: `darken($front-color, 30%)`.


## $back-color:

The color of the back part of the ribbon. Default value: `$front-color`.


## $back-width:

The width of the back part of the ribbon, in px. Default value: `40px`.


## $overlap-width:

The width of the overlap of the ribbon, in px. Default value: `30px`.


## $overlap-height:

The height of the overlap of the ribbon, in px. Default value: `20px`.


## $border-radius:

Border radius of the back part of the ribbon. Default value: `0`.


## $include-pie:

Support for CSS3 PIE (AKA: border-radius, box-shadow and others CSS3 styles for IE8/7/6). [More info](http://compass-style.org/reference/compass/css3/pie/). Remember set `$pie-behavior` with the path of the `PIE.htc` and deliver the file with the mime-type `Content-Type: text/x-component`.

Default value: `false`.




#Examples

The examples in action can be found in `templates/project/3d-ribbon-examples.html`.
    
    #ribbon-example-1{
      @include ribbon($front-width: 400px);
    }
    
    #ribbon-example-2{
      @include ribbon($front-width: 450px, $sides: left-top right-bottom); //Asimetric ribbon!
    }
    
    #ribbon-example-3{
      @include ribbon($front-width: 550px, $ribbon-height: 40px, $front-color: #8C46C3);
    }
    
    #ribbon-example-4{
      @include ribbon($front-width: 600px, $front-color: #8C46C3, $edges-color: darken(#9F4BBA, 10%), $back-color: #B952AE);
    }
    
    #ribbon-example-5{
      @include ribbon($front-width: 650px, $back-width: 20px, $overlap-width: 25px, $overlap-height: 10px);
    }
    
    #ribbon-example-6{
      @include ribbon($front-width: 650px, $back-width: 0);
    }
    
    #ribbon-example-7{
      @include ribbon($front-width: 700px, $border-radius: 5px);
    }
    
    #ribbon-example-8{
      @include ribbon(
              $front-width: 750px,
              $sides: left-bottom,
              $ribbon-height: 40px,
              $front-color: #80B5AD, 
              $edges-color: darken(#8ABD9A, 30%), 
              $back-color: #8DBF96,
              $back-width: 30px, 
              $overlap-width: 35px, 
              $overlap-height: 15px,
              $border-radius: 7px,
              $include-pie: true);
    }




