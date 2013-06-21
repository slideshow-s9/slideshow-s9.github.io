
* [How To Set Default Command Line Options?](#slideshowopt)


## How To Set Default Command Line Options?   {#slideshowopt}

The `SLIDESHOWOPT` environment variable lets
you set default command line options.

Example: Make `slides` your default output folder

~~~
$ SLIDESHOWOPT=-o slides
~~~

Example: Make S5-compatible slide show

~~~
$ SLIDESHOWOPT=-o slides -t s5blank
~~~

Example: Make your own template package the default

~~~
$ SLIDESHOWOPT=-t <your_template_manifest_here>
~~~

And than use the gem executable as usual (will use/add your command line 
options stored in `SLIDESHOWOPT`):

~~~
$ slideshow build microformats
~~~


