Jekyll Plugin for Using Pandoc-Ruby
===================================

This is a plugin for using [pandoc][] as your markdown converter
in [jekyll][].

I am No Longer Maintaining This
-------------------------------

**I switched to using [Hakyll](http://jaspervdj.be/hakyll/) a year or two ago,
and stopped using this plugin. In the meantime, Jekyll has gone through
some major updates. There are two reasonable sounding pull requests, aimed
at making the plugin work with recent updates. I am
not going to pull them, because I cannot test them, and I don't want to 
pretend to maintain something that I am not really maintaining.**

You should probably use one of the more up-to-date forks instead of this repo.

Warnings for Existing Users
---------------------------

### Jekyll < 1.0.0

Thanks to @ivotron, the plugin has been rewritten to work with Jekyll 1.0.0. The old version, which works with Jekyll < 1.0.0, can be found on the for-use-with-jekyll-pre-1.0.0 branch. 

### HTML5

After this [recent commit][html5] the plugin uses pandoc's `html5` output by
default instead of `html`. This may break your existing CSS styling. See the
[Configuration](#configuration) section if you'd like to go back to using
`html` output.

[html5]: https://github.com/dsanson/jekyll-pandoc-plugin/commit/8dd292f483cb81e008d769b4588f4cfb118b1d11

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

To tell jekyll to use pandoc to convert markdown, add the following line to
your `_config.yml`.

    markdown: pandoc

This plugin supports two configuration options for pandoc. Specify them both in
the pandoc section of your `_config.yml`.

- `format` - the output format to use, e.g., `html5` (default) and `html`.
- `extensions` - A list or hash of pandoc extensions to enable.

If none of the extensions you're using take arguments, then `extensions` can be
a list:

    pandoc:
      format: html5
      extensions: [smart, mathjax]

If an extention takes options, make extensions a hash that maps each extension
name to its argument.

    pandoc:
      format: html
      extensions:
        - smart
        - csl: 'apa.csl'
        - bibliography: 'references.bib'

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
