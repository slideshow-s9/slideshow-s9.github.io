title: Using Web Feeds to Build Planet Sites in Ruby

%css

pre {
  padding: 4px 4px 4px 4px;
  border-top: #bbb 1px solid;
  border-bottom: #bbb 1px solid;
  background: #f3f3f3;
}

%end


# Using Web Feeds to Build Planet Sites in Ruby

Agenda


* What's a Web Feed?
* What's a Planet?
* Why Planet? What's Planet Planet?
* What's Pluto?
* Reading Web Feeds in Ruby  - `RSS::Rss`
* Reading Web Feeds in Ruby  - `RSS::Atom::Feed`
* Who Cares? Let's Normalize - A Web Feed is a Web Feed is a Web Feed





# What's a Web Feed?

<img src='i/web-feed-icon.png' style='float: right;'>

A web feed (or news feed) is a simple data format
that 1) lets you publish a list of
status updates, blog postings, articles, pictures, recordings, etc
and that 2) lets others subscribe to your updates.


Example:

~~~
<feed>
  <title>Floor Drees » blog</title>
  <link href="http://www.1stfloorgraphics.nl" />
  <updated>2013-10-23T13:54:22Z</updated>
  <entry>
    <title>DevFest Vienna, Day 1 & 2: Talks, Presentations and Hacking</title>
    <link href="http://www.1stfloorgraphics.nl/2013/10/23/devfest-vienna-day-1-2-talks-presentations-and-hacking/" />
    <published>2013-10-23T13:54:22Z</published>
    <summary>A tad overdue, but still: my recap of this years Vienna DevFest...</summary>
    ...
  </entry>
  <entry>
    <title>Time for a new adventure at CheckiO</title>
    <link href="http://www.1stfloorgraphics.nl/2013/10/21/time-for-a-new-adventure-at-checkio/" />
    <published>2013-10-21T07:00:07Z</published>
    <summaray>It's time for a personal announcement - I heard that's what a blog is for anyway...</summary>
  ...
</feed>
~~~

[(Source: `1stfloorgraphics.nl/blog/feed`)](http://www.1stfloorgraphics.nl/blog/feed/atom/)



# What's a Planet?

It's a kind of Do-It-Yourself Facebook Newsfeed:

Step 1) Read a list of web feeds.

Step 2) Mix up all postings in a new page.

Step 3) Serve and enjoy.


Example: Planet Vienna.rb

![](i/planet-viennarb.png)

Example: Planet Vienna.rb - Alternative Design / Style

![](i/planet-viennarb-ii.png)



# Why Planet? What's Planet Planet?

In an age long before Facebook in the year 2004:

Planet Planet [(`planetplanet.org`)](http://www.planetplanet.org) - very first
free planet scripts and templates (by Scott James Remnant and Jeff Waugh) in Python
for reading web feeds and building new web pages;
used for Planet Gnome [(`planet.gnome.org`)](https://planet.gnome.org) ([Hackergotchi Heads](https://planet.gnome.org/heads/))
and Planet Debian [(`planet.debian.org`)](http://planet.debian.org/) (still running today!).


More Planets:

[Planet Ubuntu](http://planet.ubuntu.com)  •
[Planet Fedora](http://planet.fedoraproject.org)  •
[Planet Free Desktop](http://planet.freedesktop.org)  •
[Planet KDE](http://planetkde.org)  •
[Planet Mozilla](http://planet.mozilla.org)  •
[Planet Firefox](http://planet.firefox.com)  •
[Planet Document Foundation](http://planet.documentfoundation.org)  •
[Planet Apache](http://planet.apache.org/committers)  •
[Planet WordPress](http://planet.wordpress.org)  •
[Planet Drupal](http://drupal.org/planet)  •
[Planet Django](http://www.planetdjango.org)  •
[Planet Parrot](http://planet.parrotcode.org)  •
[Planet Haskell](http://planet.haskell.org)  •
[Planet Ruby](http://plutolive.herokuapp.com/ruby)  •
[Planet JavaScript](http://plutolive.herokuapp.com/js)  •
[Planet Dart](http://plutolive.herokuapp.com/dart)  •
[Planet Vienna.rb](http://viennarb.herokuapp.com)  •
and many many more.

Your Planet? 


# What's Pluto?

<img src='i/pluto-logo.png' style='float: right;'>

A [free planet site generator](http://feedreader.github.io) in Ruby (Yes!)
that lets you build web pages from published web feeds.

Use the `pluto` command line tool and pass in one or more planet configuration files.
Example:

~~~
$ pluto build viennarb.ini
~~~

This will

1) fetch all feeds listed in `viennarb.ini` and

2) store all entries in a local database, that is, `viennarb.db` in your working folder and

3) generate a planet web page, that is, `viennarb.html` using the blank template pack in your working folder using all feed entries from the local database.

Open up `viennarb.html` to see your planet web page. Voila!


Appendix: `viennarb.ini`

~~~
title  = Planet Vienna.rb

[viennarb]
  title   = Vienna.rb Blog
  link    = http://vienna-rb.at
  feed    = http://vienna-rb.at/atom.xml

[viennarbmeetup]
  title = Vienna.rb Meetups
  link  = http://www.meetup.com/vienna-rb
  feed  = http://www.meetup.com/vienna-rb/events/rss/vienna.rb/

[floor]
  title  = Floor Drees's Blog
  link   = http://www.1stfloorgraphics.nl/blog/
  feed   = http://www.1stfloorgraphics.nl/blog/feed/
  github = FloorD

[pxlpnk]
  title  = Andreas Tiefenthaler's Blog
  link   = http://lab.an-ti.eu
  feed   = http://lab.an-ti.eu/atom.xml
  github = pxlpnk

[abangratz]
  title  = Anton Bangratz's Blog
  link   = http://abangratz.github.io
  feed   = http://abangratz.github.io/atom.xml
  github = abangratz
  
...
~~~




# Reading Web Feeds in Ruby  - `RSS::Rss`


## 1) RSS - Really Simple Syndication / Rich Site Summary

~~~
require 'rss'
require 'open-uri'

xml = open( 'http://www.1stfloorgraphics.nl/blog/feed' ).read

feed = RSS::Parser.parse( xml )

puts "feed.class.name: #{feed.class.name}"

puts "== #{feed.channel.title} =="

feed.items.each do |item|
  puts "- #{item.title}"
  puts "  (#{item.link})"
  puts
end
~~~

Prints:

~~~
feed.class.name: RSS::Rss

== Floor Drees » blog ==

- DevFest Vienna, Day 1 & 2: Talks, Presentations and Hacking
  (http://www.1stfloorgraphics.nl/2013/10/23/devfest-vienna-day-1-2-talks-presentations-and-hacking/)

- Time for a new adventure at CheckiO
  (http://www.1stfloorgraphics.nl/2013/10/21/time-for-a-new-adventure-at-checkio/)

- DevFest Vienna Day 0, 18 October
  (http://www.1stfloorgraphics.nl/2013/10/19/devfest-vienna-day-0-18-october/)

- Can we talk about programming again?
  (http://www.1stfloorgraphics.nl/2013/10/18/can-we-talk-about-programming-again/)

- Ruby resources for those getting started
  (http://www.1stfloorgraphics.nl/2013/10/17/ruby-resources-for-those-getting-started/)

- RuPy Budapest 2013 – the day after
  (http://www.1stfloorgraphics.nl/2013/10/14/rupy-budapest-2013-the-day-after/)

- Arrrrcamp 2013 – a recap
  (http://www.1stfloorgraphics.nl/2013/10/10/arrrrcamp-2013-a-recap/)

- WordCamp Europe 2013 – a recap
  (http://www.1stfloorgraphics.nl/2013/10/06/wordcamp-europe-2013-a-recap/)

- Working towards great version control for content creators / talk excerpt #wceu 2013
  (http://www.1stfloorgraphics.nl/2013/10/06/working-towards-great-version-control-for-content-creators-talk-excerpt

- How to survive the holidays as a Techie
  (http://www.1stfloorgraphics.nl/2013/10/05/how-to-survive-the-holidays-as-a-techie/)
~~~



# Reading Web Feeds in Ruby  - `RSS::Atom::Feed`

## 2) ATOM

~~~
require 'rss'
require 'open-uri'

xml = open( 'http://www.1stfloorgraphics.nl/blog/feed/atom' ).read

feed = RSS::Parser.parse( xml )

puts "feed.class.name: #{feed.class.name}"

puts "== #{feed.title.content} =="

feed.entries.each do |entry|
  puts "- #{entry.title.content}"
  puts "  (#{entry.link.href})"
  puts
end
~~~

Prints:

~~~
feed.class.name: RSS::Atom::Feed

== Floor Drees » blog ==
- DevFest Vienna, Day 1 &amp; 2: Talks, Presentations and Hacking
  (http://www.1stfloorgraphics.nl/2013/10/23/devfest-vienna-day-1-2-talks-presentations-and-hacking/)

- Time for a new adventure at CheckiO
  (http://www.1stfloorgraphics.nl/2013/10/21/time-for-a-new-adventure-at-checkio/)

- DevFest Vienna Day 0, 18 October
  (http://www.1stfloorgraphics.nl/2013/10/19/devfest-vienna-day-0-18-october/)

- Can we talk about programming again?
  (http://www.1stfloorgraphics.nl/2013/10/18/can-we-talk-about-programming-again/)

- Ruby resources for those getting started
  (http://www.1stfloorgraphics.nl/2013/10/17/ruby-resources-for-those-getting-started/)

- RuPy Budapest 2013 &#8211; the day after
  (http://www.1stfloorgraphics.nl/2013/10/14/rupy-budapest-2013-the-day-after/)

- Arrrrcamp 2013 &#8211; a recap
  (http://www.1stfloorgraphics.nl/2013/10/10/arrrrcamp-2013-a-recap/)

- WordCamp Europe 2013 &#8211; a recap
  (http://www.1stfloorgraphics.nl/2013/10/06/wordcamp-europe-2013-a-recap/)

- Working towards great version control for content creators / talk excerpt #wceu 2013
  (http://www.1stfloorgraphics.nl/2013/10/06/working-towards-great-version-control-for-content-creators-talk-excerpt-wceu-2013/)

- How to survive the holidays as a Techie
  (http://www.1stfloorgraphics.nl/2013/10/05/how-to-survive-the-holidays-as-a-techie/)
~~~


# What's the difference?  RSS vs ATOM

| RSS                   |  ATOM                   |
| `feed.channel.title`  |  `feed.title.content`   |
| `item.title`          |  `entry.title.content`  |
| `item.link`           |  `entry.link.href`      |


RSS:

~~~
<rss version="2.0">
  <channel>
    <title>Floor Drees » blog</title>
    <link>http://www.1stfloorgraphics.nl</link>
    <lastBuildDate>Wed, 23 Oct 2013 13:54:22 +0000</lastBuildDate>
    <item>
      <title>DevFest Vienna, Day 1 & 2: Talks, Presentations and Hacking</title>
      <link>http://www.1stfloorgraphics.nl/2013/10/23/devfest-vienna-day-1-2-talks-presentations-and-hacking/</link>
      <pubDate>Wed, 23 Oct 2013 13:54:22 +0000</pubDate>
      <description>A tad overdue, but still: my recap of this years Vienna DevFest...</description>
    </item>
    ...
  </channel>
</rss>
~~~

[(Source: `1stfloorgraphics.nl/blog/feed`)](http://www.1stfloorgraphics.nl/blog/feed/)

ATOM:

~~~
<feed xmlns="http://www.w3.org/2005/Atom">
  <title type="text">Floor Drees » blog</title>
  <link rel="alternate" type="text/html" href="http://www.1stfloorgraphics.nl" />
  <updated>2013-10-23T13:54:22Z</updated>
  <entry>
    <title type="html">DevFest Vienna, Day 1 &amp; 2: Talks, Presentations and Hacking</title>
    <link rel="alternate" type="text/html" href="http://www.1stfloorgraphics.nl/2013/10/23/devfest-vienna-day-1-2-talks-presentations-and-hacking/" />
    <published>2013-10-23T13:54:22Z</published>
    <summary type="html">A tad overdue, but still: my recap of this years Vienna DevFest...</summary>
  </entry>
  ...
</feed>
~~~

[(Source: `1stfloorgraphics.nl/blog/feed/atom`)](http://www.1stfloorgraphics.nl/blog/feed/atom/)



# Who Cares? Let's Normalize - A Web Feed is a Web Feed is a Web Feed

Uniform title, link, summary, content, etc. (for standard case):

~~~
require 'feedutils'
require 'open-uri'

xml = open( 'http://www.1stfloorgraphics.nl/blog/feed' ).read 
# xml = open( 'http://www.1stfloorgraphics.nl/blog/feed/atom' ).read

feed = FeedUtils::Parser.parse( xml )

puts "feed.class.name: #{feed.class.name}"

puts "== #{feed.title} =="

feed.items.each do |item|
  puts "- #{item.title}"
  puts "  (#{item.url})"
  puts
end

~~~

Prints:

~~~
feed.class.name: FeedUtils::Feed

== Floor Drees » blog ==

- DevFest Vienna, Day 1 & 2: Talks, Presentations and Hacking
  (http://www.1stfloorgraphics.nl/2013/10/23/devfest-vienna-day-1-2-talks-presentations-and-hacking/)

...
~~~

More Ruby gems feed options:

- [feedutils](http://rubygems.org/gems/feedutils)
- [feed-normalizer](http://rubygems.org/gems/feed-normalizer)
- [simple-rss](http://rubygems.org/gems/simple-rss)
- [feedzirra](http://rubygems.org/gems/feedzirra)
- and others







