# Changelog

## Version 3.5.1 (Security)

* Fix a security vulnerability using `:quote` in combination with the
  `:escape_html` option.

  Reported by *Johan Smits*.

## Version 3.5.0

* Avoid mutating the options hash passed to a render object.

  Refs #663.

  *Max Schwenk*

* Fix a segfault rendering quotes using `StripDown` and the `:quote`
  option.

  Fixes #639.

* Fix `warning: instance variable @options not initialized` when
  running under verbose mode (`-w`, `$VERBOSE = true`).

* Fix SmartyPants single quotes right after a link. For example:

  ~~~markdown
  [John](http://john.doe)'s cat
  ~~~

  Will now properly converts `'` to a right single quote (i.e. `’`).

  Fixes #624.

* Remove the `rel` and `rev` attributes from the output generated
  for footnotes as they don't pass the HTML 5 validation.

  Fixes #536.

* Automatically enable the `fenced_code_blocks` option passing a
  `HTML_TOC` object to the `Markdown` object's constructor since
  some languages rely on the sharp to comment code.

  Fixes #451.

* Allow passing `Range` objects to the `nesting_level` option to have
  a higher level of customization for table of contents:

  ~~~ruby
  Redcarpet::Render::HTML_TOC.new(nesting_level: 2..5)
  ~~~

  Fixes #519.

## Version 3.4.0

* Rely on djb2 hashing generating anchors with non-ASCII chars.

  Fix issue [#538](https://github.com/vmg/redcarpet/issues/538).

  *Alexey Kopytko*, *namusyaka*

* Added suppport for HTML 5 `details` and `summary` tags.

  Fix issue [#578](https://github.com/vmg/redcarpet/issues/578).

  *James Edwards-Jones*

* Multiple single quote pairs are parsed correctly with SmartyPants.

  Fix issue [#549](https://github.com/vmg/redcarpet/issues/549).

  *Jan Jędrychowski*

* Table headers don't require a minimum of three dashes anymore; a
  single one can be used for each row.

* Remove escaped entities from `HTML` render table of contents'
  ids to be consistent with the `HTML_TOC` render.

  Fix issue [#529](https://github.com/vmg/redcarpet/issues/529).

* Remove periods at the end of URLs when autolinking to make sure
  that links at the end of a sentence get properly generated.

  Fix issue [#465](https://github.com/vmg/redcarpet/issues/465).

* Expose the Markdown and rendering options through a `Hash` inside
  the `@options` instance variable for custom render objects.

* Avoid escaping ampersands in href links.

  *Nolan Evans*

## Version 3.3.4

* Fix `bufprintf` to correctly work on Windows MinGW-w64 so strings
  are properly written to the buffer.

  *Kenichi Saita*

* Fix the header anchor normalization by skipping non-ASCII chars
  and not calling tolower because this leads to invalid UTF-8 byte
  sequences in the HTML output. (tolower is not locale-aware)

  *Clemens Gruber*

## Version 3.3.3

* Fix a memory leak instantiating a `Redcarpet::Render::Base` object.

  *Oleg Dashevskii*

* Fix the `StripDown` renderer to handle the `:highlight` option.

  *Itay Grudev*

* The `StripDown` renderer handles tables if the `tables` extension is
  enabled.

  *amnesia7*

* Fix Smarty Pants to avoid fraction conversions when there are several
  numbers separated with slashes (e.g. for a date).

  *Sam Saffron*

## Version 3.3.2

* Fix a potential security issue in the HTML renderer
  (Thanks to Giancarlo Canales Barreto for the heads up)

## Version 3.3.1

* Include the `Redcarpet::CLI`'s file in the gemspec to make it
  available when downloading.

## Version 3.3.0

* Fix the stripping of surrounding characters that should be removed
  during anchor generation.

## v3.2.2.4

* Relax max nesting.

## v3.2.2.3

* Change `<code>` attribute for code block metadata (language) from `class` to `data-metadata`.
  Note that this is a breaking change, though you won't face this breakage if you're using greenmat through qiita-markdown gem and updating both gems.

## v3.2.2.2

* Fix bugs in UTF-8 handling. [#3](https://github.com/increments/greenmat/pull/3) ([@gfx](https://github.com/gfx))

## v3.2.2.1

* Fix a bug where bad memory access would happen in a document starting with `@`.

## v3.2.2.0

* Update base Redcarpet version to 3.2.2.

## v3.2.0.2

* Fix missing `greenmat/version` in the gem package.

## Version 3.2.3

* Avoid rewinding content of a previous inline when autolinking is
  enabled.

  *Daniel LeCheminant*

* Fix escaping of forward slashes with the `Safe` render object (add a
  missing semi-colon).

## Version 3.2.2

* Add `no_mention_emphasis` option to disable emphasizing mentions.

## v3.2.0.0

* Initial release.
