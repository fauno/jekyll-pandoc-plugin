Jekyll Plugin for Using Pandoc-Ruby
===================================

This is a plugin for using [pandoc][] as your markdown converter
in [jekyll][].

Warning for Existing Users
--------------------------

After this [recent commit](https://github.com/dsanson/jekyll-pandoc-plugin/commit/8dd292f483cb81e008d769b4588f4cfb118b1d11), the plugin uses pandoc's `html5` output instead of `html`. This may break your existing CSS styling. See [Issue 3](https://github.com/dsanson/jekyll-pandoc-plugin/issues/3) for discussion.

Installation
------------

The plugin depends on the [pandoc-ruby][] gem, which in turn depends on
pandoc. You can install pandoc-ruby with:

    gem install pandoc-ruby

To install this plugin, copy `pandoc_markdown.rb` into the `_plugins`
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

The plugin will not work with [github pages][]. If you set
`markdown: pandoc` in your `_config.yml`, github pages will ignore this
setting, and the default markdown converter will be used.

I use github pages to mirror my official site. My official site is built
by jekyll using pandoc. I want my github mirror to be built using
rdiscount, and I don't want to maintain two separate `_config.yml`
files. My `_config.yml` file contains lines that look like this:

    markdown:  rdiscount
    pandoc:
       extensions: [smart, mathjax]

The plugin sees that the `pandoc` option has been set, and so uses
pandoc. Github pages ignores the `pandoc` option, and sees that
`markdown` has been set to rdiscount. To get the same effect, but
without passing any options to pandoc, try

    markdown:  rdiscount
    pandoc:  true

  [pandoc]: (http://johnmacfarlane.net/pandoc/
  [jekyll]: https://github.com/mojombo/jekyll
  [pandoc-ruby]: https://github.com/alphabetum/pandoc-ruby
  [github pages]: http://pages.github.com/
