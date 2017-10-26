---
layout: default
title: Code/Syntax Highlighting Helpers
---

# {{ page.title }}

<div markdown="1" class="toc">
Contents:

* [Hello, Syntax Highlighting Helper!](#intro)
* [Client-Side vs. Server-Side Syntax Highlighting](#engines)
* [Using the `code` Helpers for Syntax Highlighting](#use)
* [Questions? Comments?](#questions)
</div>

## Hello, Syntax Highlighting Helper!   {#intro}

Slide Show (S9) lets you include and syntax highlight code
with the `code` helper. Example:

```
<% code do %>
# The Greeter class
class Greeter
  def initialize(name)
    @name = name.capitalize
  end
 
  def salute
    puts "Hello #{@name}!"
  end
end
 
# Create a new object
g = Greeter.new("world")
 
# Output "Hello World!"
g.salute
<% end %>
```

becomes

<div>
<pre class="programlisting eiffel"><span class="line-numbers">   1 </span> <span class="Comment"><span class="Comment">#</span> The Greeter class</span>
<span class="line-numbers">   2 </span> <span class="Keyword">class</span> <span class="TypeName">Greeter</span>
<span class="line-numbers">   3 </span>   <span class="Keyword">def</span> <span class="FunctionName">initialize</span>(<span class="FunctionParameter">name</span>)
<span class="line-numbers">   4 </span>     <span class="Variable"><span class="Variable">@</span>name</span> <span class="Keyword">=</span> name.<span class="FunctionName">capitalize</span>
<span class="line-numbers">   5 </span>   <span class="Keyword">end</span>
<span class="line-numbers">   6 </span>  
<span class="line-numbers">   7 </span>   <span class="Keyword">def</span> <span class="FunctionName">salute</span>
<span class="line-numbers">   8 </span>     puts <span class="String"><span class="String">&quot;</span>Hello <span class="StringInterpolation"><span class="StringInterpolation">#{</span><span class="Variable"><span class="Variable">@</span>name</span><span class="StringInterpolation">}</span></span>!<span class="String">&quot;</span></span>
<span class="line-numbers">   9 </span>   <span class="Keyword">end</span>
<span class="line-numbers">  10 </span> <span class="Keyword">end</span>
<span class="line-numbers">  11 </span>  
<span class="line-numbers">  12 </span> <span class="Comment"><span class="Comment">#</span> Create a new object</span>
<span class="line-numbers">  13 </span> g <span class="Keyword">=</span> <span class="LibraryObject">Greeter</span>.<span class="FunctionName">new</span>(<span class="String"><span class="String">&quot;</span>world<span class="String">&quot;</span></span>)
<span class="line-numbers">  14 </span>  
<span class="line-numbers">  15 </span> <span class="Comment"><span class="Comment">#</span> Output &quot;Hello World!&quot;</span>
<span class="line-numbers">  16 </span> g.<span class="FunctionName">salute</span>
</pre>
</div>

## Client-Side vs. Server-Side Syntax Highlighting - Your Choice   {#engines}

Slide Show (S9) ships with three built-in syntax highlighting helper engines
letting you choose between client-side syntax highlighting in JavaScript
(the out-of-the-gem factory setting) or server-side ahead-of-time
syntax highlighting in classic Ruby.

### What's SyntaxHighlighter? 

SyntaxHighligher is a free, open-source syntax highlighter in JavaScript:

* [SyntaxHighlighter Project Site](http://alexgorbatchev.com/SyntaxHighlighter/)
* [SyntaxHighlighter Languages](http://alexgorbatchev.com/SyntaxHighlighter/manual/brushes/)
* [SyntaxHighlighter Themes](http://alexgorbatchev.com/SyntaxHighlighter/manual/themes/)

Note, if you use the SyntaxHighligher engine you will need to
use the [`s6syntax`](http://github.com/geraldb/slideshow-s6-syntax-highlighter)
template pack that includes the SyntaxHighlighter machinery or as an alternative
bundle up your own template pack.

### What's Ultraviolet? 

Ultraviolet is a free, open-source syntax highlighting engine
in Ruby that uses Textmate syntax files offering out-of-the-gem
syntax highlighting for more than fifty languages in twenty themes:

* [Ultraviolet Project Site](http://ultraviolet.rubyforge.org)
* [Ultraviolet Languages](http://ultraviolet.rubyforge.org/syntax_gallery.xhtml)
* [Ultraviolet Themes](http://ultraviolet.rubyforge.org/themes.xhtml)

To use Ultraviolet for syntax highlighting install the Ruby gem e.g.

```
$ gem install ultraviolet
```

and switch the `code-engine` setting to `uv` or `ultraviolet`.

### What's CodeRay?

CodeRay is another free, open source syntax highlighting engine
in Ruby:

* [CodeRay Project Site](http://coderay.rubychan.de)

To use CodeRay for syntax highlighting install the Ruby gem e.g.

```
$ gem install coderay
```

and switch the `code-engine` setting to `coderay`.


## Using the `code` Helpers for Syntax Highlighting   {#use}

The `code` helper lets you include and syntax highlight code inline e.g.

<table width="100%">
<tr>
  <td markdown="1" width="50%" style="vertical-align: top;">
Classic-style:

```
<% code do %> 
  puts 'Hello World!   
<% end %> 
```

</td>
<td markdown="1" style="vertical-align: top;">
Django-Style:

```
{% raw %}
{% code %} 
  puts 'Hello World!   
{% end %}
{% endraw %}
```
</td></tr></table>

or include code from a file - lets say `hello.rb`:

<table width="100%">
<tr>
  <td markdown="1" width="50%" style="vertical-align: top;">
```
<%= code 'hello.rb' %> 
```
</td>
<td markdown="1" style="vertical-align: top;">
```
{% raw %}
{{ code hello.rb }} 
{% endraw %}
```
</td></tr></table>

To select the language (default is `ruby`) use the `:lang` option e.g.

<table width="100%">
<tr>
  <td markdown="1" width="50%" style="vertical-align: top;">
```
<%= code 'effects.css', lang: => 'css' %> 
```
</td>
<td markdown="1" style="vertical-align: top;">
```
{% raw %}
{{ code effects.css lang=css }} 
{% endraw %}
```
</td></tr></table>

Note, you can also include parts of files
using [Codex-style markers](http://pragdave.blogs.pragprog.com/pragdave/2008/05/our-take-on-pre.html)
in your source (e.g. `#START:your_marker_here` and 
`#END:your_marker_here`) and you can also pass along an extra CSS class 
(`large`, `small`, `tiny`, etc.) e.g. this directive in Codex

```
:code code/meta/my_ostruct.rb[impl class=code-small] 
```

becomes in S9: 

<table width="100%">
<tr>
  <td markdown="1" width="50%" style="vertical-align: top;">
```
<%= code 'code/meta/my_ostruct.rb#impl', class:=>'small' %> 
```
</td>
<td markdown="1" style="vertical-align: top;">
```
{% raw %}
{{ code code/meta/my_ostruct.rb#impl class=small }}
{% endraw %}
```
</td></tr></table>


To select the underlying engine for syntax highlighting use the `:engine` option e.g.

<table width="100%">
<tr>
  <td markdown="1" width="50%" style="vertical-align: top;">
```
<%= code 'highlight.rb', :engine => 'sh' %> 
```
</td>
<td markdown="1" style="vertical-align: top;">
```
{% raw %}
{{ code highlight.rb  engine=sh }}
{% endraw %}
```
</td></tr></table>

or use a header to set it once e.g:

```
code-engine: sh   # or use your very own code engine here 
```

You can also use the built-in code highlighting engines 
"stand-alone" without the code "wrapper" helper. 

To use SyntaxHighlighter use:

```
<% sh do %>
  puts 'Hello World!
<% end %>
```

To use Ultraviolet use: 

```
<% uv do %>
  puts '¡Hola Mundo!
<% end %>
```

To use CodeRay use:

```
<% coderay do %>
  puts 'Hallo Welt!
<% end %>
```

Note, that the `sh`, `uv` and `coderay` helpers
only support inline code (if you want to include code use a nested include e.g.: 

```
<% sh :lang => 'css', :line_numbers => 'off' do %>
  <%= include 'gradients.css' %> 
<% end %> 
```

For more options or on how to write your own syntax highlighting 
helpers check the [source of the syntax higlighting helpers](http://github.com/slideshow-s9/slideshow/tree/master/lib/slideshow/helpers/syntax).


{% include questions.md %}
