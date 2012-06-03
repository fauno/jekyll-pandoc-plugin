Jekyll Plugin for Using Pandoc-Ruby
===================================

To install this plugin, put `pandoc_markdown.rb` into the `_plugins` directory in your site source root (if no `_plugins` directory exists, create it.)

This plugin uses the [pandoc-ruby](https://github.com/alphabetum/pandoc-ruby) gem, which in turn depends on [pandoc](http://johnmacfarlane.net/pandoc/). You can install pandoc-ruby with:

    gem install pandoc-ruby

To use pandoc-ruby, add 

    markdown: pandoc

to your `_config.yml` file. To set options, specify them in `_config.yml` like so,

    pandoc:
       extensions: [smart, mathjax]

