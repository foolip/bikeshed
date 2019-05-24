Bikeshed, a spec preprocessor
=============================

<img src="https://rawgit.com/tabatkins/bikeshed/master/docs/icon.svg" width=100 height=100 align=left>

Bikeshed is a pre-processor for spec documents,
turning a source document
(containing only the actual spec content, plus several shorthands for linking to terms and other things)
into a final spec document,
with appropriate boilerplate, bibliography, indexes, etc all filled in.
It's used on specs for CSS and many other W3C working groups,
WHATWG,
the C++ standards committee,
and elsewhere!

[![Build Status](https://travis-ci.org/tabatkins/bikeshed.svg?branch=master)](https://travis-ci.org/tabatkins/bikeshed)
[![Gitter](https://img.shields.io/badge/Gitter-Join%20Chat%20↣-blue.svg)](https://gitter.im/tabatkins/bikeshed?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)
[![Docs](https://img.shields.io/badge/docs-available-orange.svg)](https://tabatkins.github.io/bikeshed)

The processor can be easily [installed](https://tabatkins.github.io/bikeshed/#installing) and run locally (requiring no
network access unless you're updating), or accessed as a CGI without any installation at all: <https://api.csswg.org/bikeshed/>

A short overview of some of Bikeshed's features:

* [automatic linking](https://tabatkins.github.io/bikeshed/#autolinking) of terms to their definitions based on text, so you can simple write `Use <a>some term</a> to...` and have it automatically link to the `<dfn>some term</dfn>` elsewhere in the document, or in another spec entirely!
* [automatic id generation](https://tabatkins.github.io/bikeshed/#id-gen) for headings and definitions, based on their text.
* [textual shortcuts for autolinks](https://tabatkins.github.io/bikeshed/#autolink-shortcuts): [[FOO]] for bibliography entries, &lt;&lt;foo>> for grammar productions, 'foo' for CSS property names, {{foo}} for IDL terms, and more.
* [boilerplate generation](https://tabatkins.github.io/bikeshed/#boilerplate), both wholesale and piecemeal.
* [Bikeshed-flavored Markdown](https://tabatkins.github.io/bikeshed/#markdown), a slight variant that is extra-friendly to intermixing with normal HTML. (Besides the few intentional divergences, compliance with [CommonMark](http://commonmark.org) is expected.)
* a [compact syntax](https://tabatkins.github.io/bikeshed/#table-expansion) for writing property-definition tables.
* [automatic whitespace-prefix stripping](https://tabatkins.github.io/bikeshed/#pre-whitespace-stripping) from `<pre>` contents, so the contents can be indented properly in your HTML.
* [automatic IDL processing and syntax-checking](https://tabatkins.github.io/bikeshed/#idl) for `<pre class=idl>` contents, so you don't have to mark up every single significant term yourself.
* [automatic generation of railroad diagrams](https://tabatkins.github.io/bikeshed/#railroad) from `<pre class='railroad'>` contents.

Documentation Sections
----------------------

The full Bikeshed documentation is generated by Bikeshed and [accessible here](https://tabatkins.github.io/bikeshed/).

Note About Fatal Errors
-----------------------

Bikeshed generates "fatal errors" for lots of things that it wants you to fix,
but generally recovers gracefully from them anyway.
If you're getting a fatal error,
but don't have time to fix it and just need a spec **right now**,
you can force Bikeshed to generate anyway with the `-f` flag, like: `bikeshed -f spec`.

This is also sometimes useful when converting a spec to Bikeshed for the first time,
so you can see all the errors at once and fix them in whatever order is easiest,
rather than having to deal with them one-by-one with no idea when they'll end.
(You may also want to silence the warnings in this case,
to reduce visual noise until you've gotten it at least building successfully.
Use `bikeshed -qf spec`.)

Bikeshed File Extension
-----------------------

The preferred file extensions for Bikeshed source files is `bs`, like `index.bs`.
Bikeshed will automatically recognize `*.bs` files in the folder it's run in,
and assume that you want an output file of the same name with a `.html` extension.
The repository also contains a syntax highlighting script for Bikeshed source files.

(Bikeshed also recognizes files with `*.src.html` for backwards compatibility with older CSS specs,
though most such specs have switched their source file extensions to `.bs` now.
Using `.src.html` in most text editors will display the file with HTML source formatting,
which isn't generally what you want.)

License
-------

This document and all associated files in the github project are licensed under [CC0](http://creativecommons.org/publicdomain/zero/1.0/) ![](http://licensebuttons.net/p/zero/1.0/80x15.png).
This means you can reuse, remix, or otherwise appropriate this project for your own use **without restriction**.
(The actual legal meaning can be found at the above link.)
Don't ask me for permission to use any part of this project, **just use it**.
I would appreciate attribution, but that is not required by the license.
