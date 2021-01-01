## Theme Credits

The design for this theme comes from [CleanMagicMedium-Jekyll](https://github.com/SpaceG/CleanMagicMedium-Jekyll) by Lucas Gatsas.<br>
The code I started from is by [Katy Chuang](https://github.com/katychuang/CleanMagic-hakyll), who adapted CleanMagic for Hakyll.<br>
Code by other users of CleanMagic-hakyll was also helpful: [Benedikt Mayer](https://github.com/benedikt-mayer/benedikt-mayer.github.io) and [Ismail Mustafa](https://ismailmustafa.github.io).<br>
I've added support for LaTeX thanks to [Ng Wei En](https://github.com/wei2912/blog-src)'s blog, implemented with KaTeX.

I'd love to integrate more elaborate features as I get better with Hakyll.<br>
For now, it seems the best place to find tutorials is [here](https://jaspervdj.be/hakyll/tutorials.html). For help, see [here](https://help.github.com/en/github/working-with-github-pages).<br>
I still want to add an RSS feed as well as integration with Haskell's [diagrams](https://github.com/gjoncas/Haskell-DataViz) package.

## Building with Stack

A quick recap of how to construct the blog on my computer using the command line:

```
cd C:\Users\Graham\Documents\GitHub\gjoncas.github.io
stack build
stack exec CleanMagic-hakyll build  #or rebuild if you made changes to site.hs
```

Then, for a preview of the site (exit on cmd by pressing ctrl+C twice):
```
stack exec CleanMagic-hakyll watch
```

Then access the site here:

http://127.0.0.1:8000


## Editing vs. Publishing

It's slightly convoluted to go from editing to publishing and vice versa. I'm writing this so I don't forget.

To more easily navigate the localhost:8000 site, change baseurl in `site.hs`. (Don't forget to change it back after!)

About.md, Project.markdown, Research.markdown and index.html need to be in the main directory when editing.<br>
When posting, put them in `pages` and replace them with files from `site_` (About, blog, index, Projects, Research).<br>
When editing, delete html versions of posts; when posting, copy the html posts from `site_` into the posts folder.

There's probably a more efficient way to do this, but I'm just playing by ear here.

