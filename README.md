firefox-homepage-generator
--------------------

Tool to generate a dynamic version of a firefox "homepage" with tag cloud of
bookmarks and a random selection of backlog ("read later") links.

Templates and static assets in the "parts" directory will be used to construct
result in one of a few ways:

 * Build one "fat" html file with all the assets embedded in it.

 * Build html file and copy it along with separate static "assets" files into a
   target directory.

 * Produce a single "lean" html file with asset links to various external CDN
   sources (kinda bad idea, TODO).

Difference between these is caching, but likely irrelevant when loaded from a
local disk anyway.



Usage
--------------------

Doesn't need to be "installed" - just put the contents of the repo/package
anywhere, run the script to generate the page (and/or copy/link assets) in the
output path (configurable via --output-path, see also --output-format).

Examples:
```console
% ./ffhomegen.py
% ./ffhomegen.py -o ~/media/ffhome.html
% ./ffhomegen.py -f dir -o ~/media/ffhome
% ./ffhomegen.py -b ~/media/links.yaml
% firefox $(./ffhomegen.py -v)
% ./ffhomegen.py --help
```

### Requirements

 * Python 2.7 (not 3.X)
 * (optional) [yaml](http://pyyaml.org/) for parsing of "backlog" file

See http://pip2014.com/ for help with python modules' packaging.

To rebuild *.coffee, *.scss and *.jade files (not needed to just run the thing),
any suitable compiler for these formats can be used.
I use [node-based coffee-script](http://coffeescript.org/),
[libsass](https://pypi.python.org/pypi/libsass),
[pyjade](https://pypi.python.org/pypi/pyjade) + [jinja2](http://jinja.pocoo.org/).
Just typing "make" should do it with all these installed.



Links
--------------------

 * [Blog post with a picture](http://blog.fraggod.net/2014/05/12/my-firefox-homepage.html)
   (first version though, might be way out of date).

 * FF addons: [bookmarkshome](http://bookmarkshome.mozdev.org/) (really old),
   [mybookmarks](http://www.catsyawn.net/ma2ten/soft/mybookmarks_en.html)
   (remake of bookmarkshome),
   [bookmarks_html](https://addons.mozilla.org/en-US/firefox/addon/bookmarks_html/), etc.

 * FF has similar thing built-in (but default-disabled for ages now) -
   [browser.bookmarks.autoExportHTML](http://kb.mozillazine.org/Browser.bookmarks.autoExportHTML).

 * [Helpful explaination](http://stackoverflow.com/a/740183) of how ff bookmarks
   are organized in places.sqlite.

 * [Description of "frecency" metric](https://wiki.mozilla.org/User:Jesse/NewFrecency?title=User:Jesse/NewFrecency),
   used in places.sqlite, new ff versions' disk cache and maybe some other places.

 * There are some interesting upsides of building such page by hand -
   [blog post](http://utcc.utoronto.ca/~cks/space/blog/web/BookmarksAlternative) (not mine).
