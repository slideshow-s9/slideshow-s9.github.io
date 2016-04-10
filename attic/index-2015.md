---
layout: default
title: Welcome
---

# {{ page.title }}

<div class="toc" markdown="1">
Contents:

* [What's Slide Show (S9)?](#whatis)
* [Getting Started in 1-2-3 Easy Steps](#steps)
* [What's Markdown? What's Textile?](#markup)
* [What's S5? What's S6?](#s6)
* [About, License - Questions? Comments?](#about)
</div>

## What's Slide Show (S9)?   {#whatis}

A Ruby gem that lets you create slide shows and author slides in plain text
using a wiki-style markup language that's easy-to-write and easy-to-read.
The Slide Show (S9) project also collects and welcomes themes
and ships "out-of-the-gem" with built-in support
for "loss-free" gradient vector graphics themes.

## Getting Started in 1-2-3 Easy Steps   {#steps}

* Step 1: Author your slides in plain text using a wiki-style markup language
* Step 2: Build your slide show using the `slideshow` gem
* Step 3: Open up your slide show (web page) in your browser and hit the space bar to flip through your slides
* That's it. Showtime!


### Step 0: Install the `slideshow` gem

~~~
$ gem install slideshow
~~~

### Step 1: Author your slides in plain text using a wiki-style markup language

Slide Show lets you author your slides using a wiki-style markup language
that's easy-to-write and easy-to-read. Let's create some slides about best practices for web services
using REST:

~~~
# Web Services REST-Style: Universal Identifiers, Formats & Protocols

Agenda

- What's REST?
- Universal Identifiers, Formats & Protocols
- The Holy REST Trinity - Noun, Verbs, Types
- REST Design Principles 
- Architecture Astronaut REST Speak


# Representational State Transfer (REST) - Meaningless Acronym? Wordplay?

rest - n. - peace, ease, or refreshment resulting from the insight that the web works

No matter what vendors tell you - no need to "Light Up the Web" - relax - built on
an *open architecture using universal identifiers, formats & protocols and __evolving__
open standards* - no need to reinvent the wheel and sign-up for single-vendor offerings.

### Broad Definition

- Best Practices for Designing Web Services for a Unified Human and Programable Web

### Narrow Definition

- Alternative to BigCo Web Services (SOAP, WS-*) and RPC-Style Web Services (XML-RPC)
~~~

or

~~~
h1. Web Services REST-Style: Universal Identifiers, Formats & Protocols

Agenda

* What's REST?
* Universal Identifiers, Formats & Protocols
* The Holy REST Trinity - Noun, Verbs, Types
* REST Design Principles 
* Architecture Astronaut REST Speak

h1. Representational State Transfer (REST) - Meaningless Acronym? Wordplay?

rest - n. - peace, ease, or refreshment resulting from the insight that the web works

No matter what vendors tell you - no need to "Light Up the Web" - relax - built on
an *open architecture using universal identifiers, formats & protocols and _evolving_
open standards* - no need to reinvent the wheel and sign-up for single-vendor offerings.

h3. Broad Definition

* Best Practices for Designing Web Services for a Unified Human and Programable Web

h3. Narrow Definition

* Alternative to BigCo Web Services (SOAP, WS-*) and RPC-Style Web Services (XML-RPC)
~~~


Use `#` headings to start a new slide  in Markdown or `h1.` in Textile. That's it.
For more formatting options see the Markdown or Textile reference.


### Step 2: Build your slide show using the `slideshow` gem

Run `slideshow` to build your slide show. The `slideshow` gem
expects the name of your slide show source document (e.g. `rest`)
without the `.markdown` or `.textile` ending and will build a web page
(e.g. [`rest.html`](demos/rest.html)
that is an all-in-one-page handout and a live slide show all at once.

~~~
$ slideshow build rest

=> Preparing slideshow 'rest.html'...
=> Done.
~~~

### Step 3: Open up your slide show in your browser

Open up your slide show [`rest.html`](demos/rest.html)
in your browser (Firefox, Chrome, Opera, Safari, and others) and hit F11 to switch 
into full screen projection and hit the space bar or the right arrow, down arrow
or page down key to flip through your slides.

<a href="demos/rest.html"><img src="i/slideshow.png"></a>

That's it. Voila.

### Bonus: Try some different templates/theme packs

* [S6 PDF Theme](demos/tutorial.pdf.html) -> [PDF](demos/tutorial.pdf)
* [Google HTML5 Slides Theme](demos/packs/g5/tutorial1.html5.html)
* [S5 Blank](demos/packs/s5/tutorial1.html)
* [Slidy W3C Blue Theme](demos/packs/slidy/tutorial1.w3c.html)
* [More »](gallery.html)

## What's Markdown? What's Textile?   {#markup}

Markdown is a wiki-style markup language that's easy-to-write and easy-to-read and
that lets you author web pages in plain text. More:

* [Markdown Quick Start](http://daringfireball.net/projects/markdown/basics)
* [Markdown Reference](http://daringfireball.net/projects/markdown/syntax)

Textile is another wiki-style markup language that's easy-to-write and easy-to-read and
that lets you author web pages in plain text. More:

* [Textile Reference](http://redcloth.org/textile/)


## What's S5? What's S6?   {#s6}

Simple Standards-based Slide Show System (S5) is a classic public domain (free, open source)
slide show package inspired by Opera Show and others that works in all modern browsers
without any plugin required because it includes its own slide show machinery in JavaScript.
(Use the [`s5blank`](https://github.com/slideshow-s9/slideshow-s5-blank)
or [`s5themes`](https://github.com/slideshow-s9/slideshow-s5-themes) theme pack
to create S5 slide shows.)

* [S5 Project Site](http://meyerweb.com/eric/tools/s5)

S6 is the rewrite of S5 using
the jQuery JavaScript library - offering easier to understand and easier
to extend code. Add plugins, effects and more. Contributions welcome!

* [S6 Project Site](https://github.com/slidekit/s6)

Keyboard controls:

| Action               | Key |
| -------------------- | --- |
| Go to next slide     | Space Bar, Right Arrow Down Arrow, Page Down  |
| Go to previous slide | Left Arrow, Up Arrow, Page Up |
| Go to first slide    | Home |
| Go to last slide     | End |
| Toggle between slideshow and outline view (`Ø`) | T |
| Show/hide slide controls (`Ø` `«` `»`)  | C, Move mouse to bottom right corner |


## About, License   {#about}

Gerald Bauer and contributors designed and developed the `slideshow` gem.
See the change log for contributions and credits.

License. The slide show scripts and templates are dedicated to the public domain.
Use it as you please with no restrictions whatsoever.

{% include questions.md %}
