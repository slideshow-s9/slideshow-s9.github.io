---
layout: default
title: Command Line Reference
---

# {{ page.title }}

<div class="toc" markdown="1">
Contents:

* [`build` Command](#build)
* [`list` Command](#list)
* [`install` Command](#install)
* [`new` Command](#new)
* [Questions? Comments?](#questions)
</div>


```
SYNOPSIS
    slideshow [global options] command [command options] [arguments...]

VERSION
    3.0.0

GLOBAL OPTIONS
    -c, --config=PATH - Configuration Path (default: ~/.slideshow)
    --verbose         - (Debug) Show debug messages
    --version         - Show version

COMMANDS
    build, b           - Build slideshow
    install, i         - Install template pack
    list, ls, l        - List installed template packs
    new, n             - Generate quick starter sample
    about, a           - (Debug) Show more version info
    help               - Shows a list of commands or help for one command
```


### `build` Command  {#build}

```
NAME
    build - Build slideshow

SYNOPSIS
    slideshow [global options] build [command options] FILE

COMMAND OPTIONS
    --h1                    - Set Header Level to 1 (default)
    --h2                    - Set Header Level to 2
    --takahashi             - Allow // for slide breaks
    --slide                 - Use only !SLIDE for slide breaks (Showoff Compatible)
    -o, --output=PATH       - Output Path (default: .)
    -t, --template=MANIFEST - Template Manifest (default: s6)

EXAMPLES
    slideshow build microformats.text
    slideshow build microformats.text -o slides     # Output slideshow to slides folder
    slideshow build microformats.text -t s5blank    # Use your own slide show templates (e.g. s5blank)
```


### `list` Command  {#list}

```
NAME
    list - List installed template packs

SYNOPSIS
    slideshow [global options] list [command options] 

EXAMPLES
    slideshow list
    slideshow ls
```


### `install` Command   {#install}

```
NAME
    install - Install template pack

SYNOPSIS
    slideshow [global options] install [command options] MANIFEST

COMMAND OPTIONS
    -a, --all - Template Packs (s5blank, s5themes, slidy, g5, csss, deck.js, impress.js)

EXAMPLES
    slideshow install impress.js
    slideshow install https://raw.github.com/slideshow-s9/slideshow-impress.js/master/impress.js.txt
```


### `new` Command   {#new}

```
NAME
    new - Generate quick starter sample

SYNOPSIS
    slideshow [global options] new [command options] 

COMMAND OPTIONS
    -o, --output=PATH       - Output Path (default: .)
    -t, --template=MANIFEST - Template Manifest (default: welcome)

EXAMPLES
    slideshow new
    slideshow new -t impress.js
```


{% include questions.md %}

