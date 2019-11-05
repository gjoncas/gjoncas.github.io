## Theme Credits

The design for this theme comes from [CleanMagicMedium-Jekyll](https://github.com/SpaceG/CleanMagicMedium-Jekyll) by Lucas Gatsas.<br>
The code I started from is by [Katy Chuang](https://github.com/katychuang/CleanMagic-hakyll), who adapted CleanMagic for Hakyll.<br>
Code by other users of CleanMagic-hakyll was also helpful: [Benedikt Mayer](https://github.com/benedikt-mayer/benedikt-mayer.github.io) and [Ismail Mustafa](https://ismailmustafa.github.io).

I am still having problems supporting Unicode characters, or even apostrophes.<br>
I'd like to add support for LaTeX -- which should be possible, just a nightmare to code.<br>
I wanted to change the menus to black, but I spent a ton of time on this and finally gave up.

I'd love to integrate more elaborate features as I get better with Hakyll.<br>
For now, it seems the best place to find tutorials is [here](https://jaspervdj.be/hakyll/tutorials.html). For help, see [here](https://help.github.com/en/github/working-with-github-pages).

## Building with Stack

A quick recap of how to construct the blog on my computer using the command line:

```
cd C:\Users\Graham\Documents\GitHub\gjoncas.github.io
stack build
stack exec CleanMagic-hakyll build  #or rebuild if you made changes to site.hs
```

Then, for a preview of the site:
```
stack exec CleanMagic-hakyll watch
```

Then access the site at:

http://127.0.0.1:8000


## Editing vs. Publishing

It's slightly convoluted to go from editing to publishing and vice versa. I'm writing this so I don't forget.

To more easily navigate the localhost:8000 site, change baseurl in `site.hs`. (Don't forget to change it back when publishing!)

About.md, Contact.markdown, and the original index.html need to be in the main directory when editing & building.<br>
When publishing, put them in the pages folder, and replace them with the files from site_ (About, Research, Projects, blog, index).<br>
When editing, delete html versions of posts; when publishing, copy the html posts from site_ into the posts folder.

There's probably a more efficient way to do this, but I'm just playing by ear here.

