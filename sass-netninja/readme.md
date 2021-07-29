

Git clone https://github.com/iamshaunjp/sass-playlist.git

# Set Up

Download Prepros https://prepros.io/downloads

# Set Up Project 

-Index.html 
-styles.scss

Click on styles.scss in prepros with process automatically ticked
Click Process File
Notification saying successful should pop up. 

In VS code a new file should appear called styles.css

Add practice code to scss file 

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


 ```
.rule {
  Color: red;
}
.rule a {
  Color: blue;
}
.rule a Span {
  Color: pink;
}
```


## Variables 

Example of use 
- Adding hexcodes for colour
- Using a specific font size 


Advantage is that you can change it in one place and all CSS that uses that variable name will change

Variables start with a dollar sign
Example: 
$deepBlue: #032f3e;
$sectionHeading: 24px;

We can then use this in our Scss when we want to use that Hexcode

```
// Variables
 
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

# Nested Styles


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