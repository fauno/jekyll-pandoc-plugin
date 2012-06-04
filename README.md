Jekyll Plugin for Using Pandoc-Ruby
===================================

This is a plugin for using [pandoc][] as your markdown converter
[jekyll][].

Installation
------------

The plugin depends on the [pandoc-ruby][] gem, which in turn depends on
pandoc. You can install pandoc-ruby with:

    gem install pandoc-ruby

To install the plugin, copy `pandoc_markdown.rb` into the `_plugins`
directory in your site source root (if no `_plugins` directory exists,
create it.)

Configuration
-------------

To tell jekyll to use pandoc to convert markdown, add

    markdown: pandoc

to your `_config.yml` file. If you want to pass options to pandoc, you
can add something like

    pandoc:
       extensions: [smart, mathjax]

to your `_config.yml` file. (For how to deal with complex options, take
a look at the [pandoc-ruby][] documentation.)

Github Pages
------------

The plugin will not work with github pages. If you set
`markdown: pandoc` in your `_config.yml`, then, on github pages, that
will be ignored, and your pages will be converted with the default
markdown converter.

As a partial work around, if you set your preferred github-approved
markdown converter in `_config.yml` and *also* set the `pandoc`
variable, then the plugin will locally use pandoc to convert markdown.
So, for example, a `_config.yml` containing both

    markdown:  rdiscount
    pandoc:
       extensions: [smart, mathjax]

will be converted using rdiscount on github pages, and pandoc locally.
To get the same effect, but without passing any options to pandoc, try

    markdown:  rdiscount
    pandoc:  true

  [pandoc]: (http://johnmacfarlane.net/pandoc/
  [jekyll]: https://github.com/mojombo/jekyll
  [pandoc-ruby]: https://github.com/alphabetum/pandoc-ruby
