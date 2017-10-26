---
layout: default
title: Plugins, Helpers and Extensions
---

# {{ page.title }}

<div class="toc" markdown="1">
Contents:

* [Using Embedded Ruby (ERB) Helpers in Your Slides](#lib)
* [Built-In Helpers](#builtin)
* [Code/Syntax Highlighting Helpers](#code)
* [How to Create Your Own Helpers](#dev)
* [Questions? Comments?](#questions)
</div>


## Using Embedded Ruby (ERB) Helpers in Your Slides   {#lib}

Slide Show (S9) includes support for plugins and helpers
and lets you use Embedded Ruby (ERB) in your slide source. Example:

```
## Today's Date

<%= Date.today %> 
```

If you want to use your own helpers put your code in the `./lib`
folder (or any subfolders) and your code gets loaded on startup.

Note, as an alternative syntax for Embedded Ruby (ERB) helpers you can also
use a Django-style syntax using `{% raw %}{{ }}{% endraw %}`. Example:

```
{% raw %}
## Today's Date

{{ Date.today }}
{% endraw %}
```

## Built-In Helpers   {#builtin}

* `include`     -  Lets you include text. Example:

<table width="100%">
<tr>
  <td markdown="1" width="50%" style="vertical-align: top;">
Django-style helper syntax:

```
{% raw %}
{{ include help.txt }}
{% endraw %}
```
</td>
<td markdown="1" style="vertical-align: top;">
Classic helper syntax:

```
<%= include 'help.txt' %>
```
</td></tr></table>


* `google_analytics` - Lets you add tracker code for Google Analytics. Example:

<table width="100%">
<tr>
  <td markdown="1" width="50%" style="vertical-align: top;">
Django-style:

```
{% raw %}
{{ google_analytics code=UA-YOUR-CODE-HERE }}
{% endraw %}
```
</td>
<td markdown="1" style="vertical-align: top;">
Classic:

```
<%= google_analytics :code => 'UA-YOUR-CODE-HERE' %>
```
</td></tr></table>


* `help`  - Lets you add key control help information for the S6 slide show machinery. Example:

<table width="100%">
<tr>
  <td markdown="1" width="50%" style="vertical-align: top;">
Django-style:

```
{% raw %}
{{ help }}
{% endraw %}
```
</td>
<td markdown="1" style="vertical-align: top;">
Classic:

```
<%= help %>
```
</td></tr></table>

* `left`/`right` - Lets you use two-column layouts in your slides. Example:

<table width="100%">
<tr>
  <td markdown="1" width="50%" style="vertical-align: top;">
Django-style:

```
{% raw %}
{% left %}

### Java is

* Strongly,
* Statically,
* Manifestly

typed.
{% end %}

{% right %}

### Ruby is

* Strongly,
* Dynamically,
* Implicitly

typed.
{% end %}
{% endraw %}
```
</td>
<td markdown="1" style="vertical-align: top;">
Classic:

```
<% left do %>

### Java is

* Strongly,
* Statically,
* Manifestly

typed.
<% end %>

<% right do %>

### Ruby is

* Strongly,
* Dynamically,
* Implicitly

typed.
<% end %>
```
</td></tr></table>

* `step`  - Lets you wrap a block into a div for incremental display using steps. Example:

<table width="100%">
<tr>
  <td markdown="1" width="50%" style="vertical-align: top;">
Django-style:

```
{% raw %}
{% step %}
* Catching all inappropriate operations on a type, either at
  * compile time, or
  * run time
{% end %}
{% endraw %}
```
</td>
<td markdown="1" style="vertical-align: top;">
Classic:

```
<% step do %>
* Catching all inappropriate operations on a type, either at
  * compile time, or
  * run time
<% end %>
```
</td></tr></table>


* `content_for`  - Lets you add content to your templates from your source a la Rails.

In your slide source use: 
  
```
<% content_for :head do %> 
  your content here e.g. more meta tags; javascript includes etc. 
<% end %> 
```

In your template use: 

```
<%= content_for :head %>
```

and it will include the marked content from your source.
Note, you can use `:foo`, `:bar` or whatever key you 
want instead of `:head` and also note a la Rails you can use the same 
key as many times as you want. The new content just gets added. 


## Code/Syntax Highlighting Helpers   {#code}

Use the `code` helper to include and syntax highlight code. [More »](code.html)

## How to Create Your Own Helpers   {#dev}

Let's create a helper called `image` as a shortcut for
adding embedded images to your slides in Markdown syntax.

Let's create a new Ruby script (file) e.g. `markdown_helper.rb`
and let's pack our new helper into a module named `MarkdownHelper`
Example:

```
module MarkdownHelper
  
  # helper/shortcut for adding embedded image to slide in markdown syntax:
  #  ![alt text](/path/to/img.jpg "Title")
  #
  #  use it like:
  #  <%= image 'friendsbadge.png' %>
  #
  #  note: alternate text (alt) and title are optional
  
  def image( path, alt="", title="" )
    %Q{![#{alt}](#{path} "#{title}")} 
  end
  
end
```

Almost done. Two more steps. Include your code into
the class `Slideshow::Gen`. Add this snippet to the end of your
Ruby script:

```
class Slideshow::Gen
  include MarkdownHelper
end
```

Lastly, make sure your Ruby script (that is, `markdown_helper.rb`)
resides in the `./lib`
folder (or any subfolders) of your working folder
and your code will get loaded on startup and is ready for use in your
slides. Example:
 
```
<%= image 'friendsbadge.png' %>
```

Or Django-style:

```
{% raw %}
{{ image friendsbadge.png }}
{% endraw %}
```

That's it. For more samples, check the
[source of the plugin helpers](http://github.com/slideshow-s9/slideshow-plugins).


{% include questions.md %}
