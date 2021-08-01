# Net Ninja SASS Tutorial 

## Setup Instructions

- Git clone https://github.com/iamshaunjp/sass-playlist.git


- Download Prepros https://prepros.io/downloads

### Set Up Project 

- Index.html 
- styles.scss

- Click on styles.scss in prepros with process automatically ticked
- Click Process File
- Notification saying successful should pop up. 

In VS code a new file should appear called styles.css

- Add practice code to scss file 

```
.rule{
    Color:red;
    a{
    Color:blue;
    Span{
        Color:pink;
    }
}
} 

``` 

This could appear in css file as css


.rule {
  Color: red;
}
.rule a {
  Color: blue;
}
.rule a Span {
  Color: pink;
}



## File Structure
### @import 

You can add Variables, Mixins and main styles into different files by importing them

- Create new files
	- variables.scss
	- mixins.scss
	- reset.scss

- Bring up prepros and remove the auto compile tick box so a new css folder isnt created. Leave the tick in main scss file. 

- Copy mixins and variables into the new files. 
- Move the reset folder into the scss folder

- import files into main scss folder

``` 
@import 'reset';
@import 'variables';
@import 'mixins'; 
 
```


## Variables 

Example of use 
- Adding hexcodes for colour
- Using a specific font size 


Advantage is that you can change it in one place and all CSS that uses that variable name will change

* Variables start with a dollar sign 

Example: 
$deepBlue: #032f3e;
$sectionHeading: 24px;

We can then use this in our Scss when we want to use that Hexcode

## Variables
 
``` 
$hotPink: #e42491;
 
#main-nav{
  background: $hotPink;
}
 
```

```
// Variables 
 
$hotPink: #e42491;
$sectionHeading: 24px;
 
section h1 {
  font-size: $sectionHeading;
  color: $hotPink;
}
 
#main-nav{
  background: $hotPink;
}
 
```

## Nested Styles


Takes a lot less time to create styles 
Keeps all the elements of a section of the website in one block of code so its easier to change later on. 

Navbar Example

```
// Variables
 
$hotPink: #e42491;
$sectionHeading: 24px;
$offWhite: #f8f9fb;
 
#main-nav{
  background: $hotPink;
  ul{
     width: 100%
  }
  li {
    float: left;
    width: 14%;
  }
  a{
    color: $offWhite;
    text-decoration: none;
    padding: 16px;
    display: block;
    text-align: center;
  }
}
 
// end main nav

// To clear float height issue
#main-nav ul:after{
content: "";
display:block;
clear:both;
}   
```

## Mixins 

A chunk of reusable CSS we can inject into our code. 
It creates a rule that we can use for other parts of our code. 
For example if you want to style pictures in a certain way but add slight changes you can make a mixin and then add additional rules. 

This saves time and repeating code. 
You can also pass through variables or arguments to change the output. 

To use 
create mixins.scss in scss file 

* Mixin start with a @

``` 
$bannerHeading: 46px;
$bannerHeading: 46px;
@mixin banner{
  width: 100%;
  position: relative;
  color: white;
  .banner-content{
    position: absolute;
    top: 50px;
    width: 100%;
  }
  img{
    width: 100%;
  }
span {
  font-size: $bannerHeading;
  display: block;
  text-transform: uppercase;
  font-weight: bold;
}
 
span.title{
  font-weight: normal;
  margin-bottom:30px;
  }
}
 
```
* Underneath add @include to the name of what you want to use it in. 


```
.lead-banner{
  @include banner;
text-align: right;
}
 
.lessons-banner{
  @include banner;
  text-align: left;
 
  li{
    text-transform: uppercase;
    font-size: 20px;
    max-width: 500px;
    margin: 60px 0;
  }
}

```
## Pseudo Classes

These can be used to add in extra affects such as hover they use &: hover 

```
.button {
  &:visited { }
  &:hover { }
  &:active { }
}

```
The :visited selector is used to select visited links.
Tip: Use the :link selector to style links to unvisited pages, the :hover selector to style links when you mouse over them, and the :active selector to style links when you click on them.


```
  
  a{
    color: $offWhite;
    text-decoration: none;
    padding: 16px;
    display: block;
    text-align: center;
	&:hover{
	background: #333;
  }
}

```

## Math Operators


You can use: 
Addition 
Subtraction
Multipllication 
Division 

This helps give exact numbers when aligning things. 

```
  li {
    float: left;
    width: 14%;
  }
 
``` 
Becomes 
``` 
  li {
    float: left;
    width: (100% /6);
  }
```

## Grid System using mixins

```
    <section id="projects">
      <div class="wrapper">
        <h1>Our Projects</h1>
        <ul>
          <li><img src="http://placehold.it/150x150" /></li>
          <li><img src="http://placehold.it/150x150" /></li>
          <li><img src="http://placehold.it/150x150" /></li>
          <li><img src="http://placehold.it/150x150" /></li>
          <li><img src="http://placehold.it/150x150" /></li>
          <li><img src="http://placehold.it/150x150" /></li>
          <li><img src="http://placehold.it/150x150" /></li>
          <li><img src="http://placehold.it/150x150" /></li>
          <li><img src="http://placehold.it/150x150" /></li>
          <li><img src="http://placehold.it/150x150" /></li>
          <li><img src="http://placehold.it/150x150" /></li>
          <li><img src="http://placehold.it/150x150" /></li>
        </ul>
      </div>
```

``` 
#projects li{
  @include grid(6, 2%);
  img{
    width: 100%;
  }
}
```

Or for less boxes
``` 
#projects li{
  @include grid(4, 3%);
  img{
    width: 100%;
  }
}
``` 
// Grid system for placeholders
 
``` 
@mixin grid($cols, $mgn){
  float: left;
  width: ((100% - (($cols - 1) * $mgn)) / $cols );
  margin-right: $mgn;
  margin-bottom: $mgn;
  &:nth-child(#{$cols}n){
    margin-right: 0;
  }
}
```

## Functions

You can use functions to change the colours of things

Functions: https://sass-lang.com/documentation/modules 

lighten($color, $amount) - Lightens the colour

 ``` 
  a{
    text-decoration: none;
    color: $hotPink;
    font-weight: bold;
    &:hover{
      color: lighten($hotPink, 20);
    }
  }
 ``` 

darken($color, $amount)-  - Darkens the colour
 ``` 
    &:hover{
      background-color: darken($hotPink, 10%);
    }
  }

 ``` 
transparentize($color, $amount) - Makes the item transparent so you can see through it. 
 ``` 
    &:hover{
      background-color: transparentize($hotPink, 0.1);
    }
  }
 ``` 
opacify($color, $amount) - adds to the opacity 
 ``` 
    &:hover{
      background-color: opacify(rgba(255,45,98,0.5), 0.2);
    }
  }
 ``` 

invert($color, $weight: 100%) - Inverts the colour
 ``` 
 
    &:hover{
      
      color: invert($hotPink, 40%);
    }
  }
 ``` 
complement($color); - Generates the compliment of that colour

 ``` 
    &:hover{
      
      color: complement($teal);
    }
  }

 ``` 
mix($color, $color, %) - Mixes two colours together, you can add the percentage which adds the amount of the first colour.
 ``` 
    &:hover{
      background-color: mix($hotPink, $teal, 30%);
    }
 ``` 
You can combine the functions aswell
 ``` 
    &:hover{
      background-color: mix(complement($hotPink), $teal, 30%);
    }
 ``` 


If statements 

Can be used for more complicated media queries with max and min width 

Use spread operator to say however many arguments. 
Use length to find out how many arguments there are

```

@mixin mQ($args...){
  @if length($args) == 1{
    @media screen and (max-width: nth($args, 1)){
      @content;
    }
  }
  @if length($args) == 2{
    @media screen and (max-width: nth($args, 1)) and (min-width: nth($args, 2)){
      @content;
    }
  }
}

```




