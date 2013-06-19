---
layout: default
title: Template Reference
---

# {{ page.title }}


Create your own templates (use `headers`, `slides`, `name`, etc.)

## Headers 

Use `@headers` to reference headers (such as title, author, etc.) from your slide source
(or from your `slideshow.yml` configuration) in your templates.

Example:

~~~
<meta name="author" content="<%= @headers['author']%>">

<title><%= @headers['title'] %> | by <%= @headers['author']%></title>
~~~

Example 2:

~~~
<div class='slide'>
  <h1><%= @headers['title'] %></h1>
  <h2><%= @headers['subtitle'] %></h2>
  <h3><%= @headers['author']%></h3>
  <h4><%= @headers['company']%></h4>
</div>
~~~

## Slides

Use `@slides` to reference your slides. A `slide` includes the following fields:

* `content` 
* `header`   => Optional Header                    
* `content_without_header`   => (TODO: _Add Alias_) Optional Content Block without Header (`content = header + content_without_header`)  
* `classes`   =>  Style Classes (e.g. `fullscreen scroll`)  
* `data_attributes`  => HTML5 Data Attributes (e.g. `data-x='1200' data-y='600' data-rotate='180'`)

Example:

~~~
<% @slides.each do |slide| %>
  <div class='slide'>
     <%= slide.content %>
  </div>
<% end %>
~~~

Example 2:

~~~
<% @slides.each do |slide| %>
  <div class='slide <%= slide.classes %>'>
     <header><%= slide.header %></header>
     <section>
        <%= slide.content_without_header %>
     </section>
  </div>
<% end %>
~~~

## Filename

Use `@name` to reference the basename of the passed in file e.g. `microformats.text` becomes `microformats`.

Example:

~~~
<link rel="stylesheet" href="<%= "#{@name}.css" %>">
~~~


{% include questions.md %}
