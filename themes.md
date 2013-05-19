---
layout: default
title: Gradient Themes
---

# {{ page.title }}

<div markdown="1" class="toc">
Contents:

* [How To Use Gradient Themes for the Built-In S6 Template Pack?](#use)
* [Questions? Comments?](#questions)
</div>

## Browse by Color

<a href="g/gradient-styles-red.svg" target="gallery">Red (SVG)</a> | 
<a href="gradient-styles-red.html" target="gallery">Red (CSS3)</a> | 
<a href="g/gradient-styles-blue.svg" target="gallery">Blue</a>

## Browse by Style

<a href="g/gradient-diagonal.svg" target="gallery">Diagonal</a> | 
<a href="g/gradient-top-bottom.svg" target="gallery">Top Bottom</a> | 
<a href="g/gradient-left-right.svg" target="gallery">Left Right</a> | 
<a href="g/gradient-repeat.svg" target="gallery">Repeat</a> | 
<a href="g/gradient-radial.svg" target="gallery">Radial</a> | 
<a href="g/gradient-radial-off-center.svg" target="gallery">Radial Off Center</a> | 
<a href="g/gradient-radial-repeat.svg" target="gallery">Radial Repeat</a>

## Theme Preview

<iframe id="gallery" name="gallery"
        src="g/gradient-styles-red.svg"
        width="100%" height="60%" frameborder="0"></iframe>

## How To Use Gradient Themes for the Built-In S6 Template Pack?   {#use}

You can define your gradient theme in plain text in the slide show source in the header using
a simple CSS-style name value pair (if you use the built-in S6 templates).

Example 1: Use `top-bottom` gradient theme with the colors red and black

~~~
gradient: top-bottom red black
~~~

*Themes*. The built-in predefined gradient themes include: `diagonal`,
`top-bottom`, 
`left-right`, 
`repeat`,  
`radial`, 
`radial-off-center`, 
`radial-repeat`.

*Colors*. You can use whatever colors CSS supports e.g. pre-defined colors such as `red`, 
`maroon` or self-defined colors such as `#0e1f5b`, `#3b5998`.


Example 2: Use pre-defined CSS colors (with default `diagonal` gradient theme)

~~~
gradient-colors: green lime
~~~

Example 3: Use self-defined colors (with default `diagonal` gradient theme)

~~~
gradient-colors: #0e1f5b #3b5998
~~~

Example 4: Use `radial` gradient theme and facebook colors

~~~
gradient: radial #0e1f5b #3b5998
~~~

Example 5: Just change gradient theme and use default colors, that is, `red` and `orange`

~~~
gradient-theme: repeat
~~~

That's it.


{% include questions.md %}
