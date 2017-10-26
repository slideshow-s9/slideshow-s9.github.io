---
layout: default
title: Settings Reference
---

# {{ page.title }}

Use `slideshow.yml` in your working folder or in your home folder
to configure the `slideshow` gem.


## Headers

The `headers` section lets you set default/fallback headers. Example:

```
headers:
  generator: "<%= Slideshow.generator %>"
  author: Your Name Here
  email: Your Email Here
  company: Your Company Here
  title: Your Title Here
  subtitle: Your Subtitle Here
  footer: Your Footer Here
  subfooter: Your Subfooter Here
  date: "<%= Date.today %>"
```

## Fetch - Template Pack Shortcuts

The `fetch` section lets you configure template pack shortcuts. Example:

```
fetch:
  g5: https://raw.github.com/slideshow-s9/slideshow-google-html5-slides/master/g5.txt
  csss: https://raw.github.com/slideshow-s9/slideshow-csss/master/csss.txt
  deck.js: https://raw.github.com/slideshow-s9/slideshow-deck.js/master/deck.js.txt
  impress.js: https://raw.github.com/slideshow-s9/slideshow-impress.js/master/impress.js.txt
```

Now you can use

```
slideshow install g5
```

Instead of

```
slideshow install https://raw.github.com/slideshow-s9/slideshow-google-html5-slides/master/g5.txt
```

## Filters

The `filter` section lets you configure filters to run before the markup processing. Example:

```
filters:
  - skip_end_directive
  - directives_bang_style_to_percent_style
  - directives_percent_style
  - comments-percent-style
  - leading-headers
  - erb-django-style
  - erb-rename-helper-hack
  - erb
```


{% include questions.md %}
