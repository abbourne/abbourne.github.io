---
layout: page
title: Hugo's Markdown Extensions
date: 2013-01-20 21:04
tags: [Markdown, Pandoc, Hugo]
# mathjaxPath: "https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.6/MathJax.js" # Specify MathJax path
mathjaxConfig: TeX-MML-AM_CHTML
mathjax: true
---

## Introduction

This article focuses on markdown as supported by Hugo and Pandoc.
Here are a few good Markdown references and tutorials:

* [Markdown Guide](https://www.markdownguide.org/)
* [Wikipedia Markdown entry](https://en.wikipedia.org/wiki/Markdown)
* [CommonMark](https://commonmark.org/) - the markdown "standard"

### Hugo's Markdown

Hugo uses the [GoldMark](https://github.com/yuin/goldmark/) as it's default Markdown processor. Goldmark supports the [CommonMark](https://commonmark.org/) standard, along with:

* Tables, Strikethrough, Autolinks, TaskLists from [GitHub-Flavored Markdown](https://github.github.com/gfm/)
* Definition Lists and Footnotes from [PHP Markdown Extra](https://michelf.ca/projects/php-markdown/extra/)
* Special typographic characters from [SmartyPants](https://daringfireball.net/projects/smartypants/)
* Embedded HTML may be enabled in the [Hugo Site Configuration](https://gohugo.io/getting-started/configuration-markup/)
* Attribute lists on headings and block elements to add styling. See [Hugo Site Configuration](https://gohugo.io/getting-started/) and [Easier writing](https://www.brycewray.com/posts/2021/02/new-hugo-easier-writing/)

Hugo Goldmark also supports:

* MathJax support, including AsciiMath, with the appropriate support in the theme layouts
* Syntax highlighting in fenced code blocks using [Chroma](https://github.com/alecthomas/chroma) syntax highlighter. See [Hugo Syntax Highlighting](https://gohugo.io/content-management/syntax-highlighting) for details.
* Emoji Support. Set `enableEmoji` to `true` in the [main site configuration](https://gohugo.io/getting-started/configuration/#all-configuration-settings). For a list of emoji see [Emoji Cheat Sheet](https://www.webfx.com/tools/emoji-cheat-sheet/)

### Pandoc's Markdown

See [Pandoc's Markdown](https://pandoc.org/MANUAL.html#pandocs-markdown) for details.

## Markdown Formats

There are many variants of Markdown formats, and each processor may support a range of extensions, and interpret the Markdown specifications in somewhat different ways. The main formats include:

* [CommonMark](https://commonmark.org/) is a standardization effort intended to create a robust specification. However many commonly used extensions (eg. tables, emoji, attribute lists,  ) are not yet covered.
* [GitHub Flavored Markdown](http://github.github.com/github-flavored-markdown/) - a small set of extensions CommonMark, and very heavily used
* [Pandoc](https://pandoc.org/MANUAL.html#pandocs-markdown)  - extensive set of extensions, but strays from the original markdown syntax and extensions somewhat
* [Markdown](http://daringfireball.net/projects/markdown/syntax) - this is the classic original version, now obsoleted by CommonMark
* [Multimarkdown](http://fletcher.github.com/peg-multimarkdown/mmd-manual.pdf) - the original extension to Markdown
* [Kramdown](http://kramdown.rubyforge.org/syntax.html) - extensive set of extensions based on [PHP markdown Extra package](http://michelf.ca/projects/php-markdown/extra/) and [Maruku](http://maruku.rubyforge.org)

## Markdown Processors

There are many flavours of [Markdown](http://daringfireball.net/projects/markdown/syntax), each with its own
characteristics. My requirements included the ability to support tables, and the ability to generate PDF files as well
as html.

Major Markdown processors, and the variants of Markdown they support include:

* [Pandoc](http://johnmacfarlane.net/pandoc)

  * Is a general purpose document converter. Markdown is just one of many formats supported.
  * Considered the "swiss army knife" of documents conversation, given the large number of formats, and the large number of conversion and formatting options it supports.
  * Very popular processor, widely supported
  * Written in Haskell. May be slow for large sites
  * Supports an enhanced Markdown with many extensions
  * Converts to many file formats:

    * XHTML, HTML5, and HTML slide shows
    * Microsoft Word docx, OpenOffice/LibreOffice ODT, OpenDocument XML
    * EPUB, [DocBook](http://www.docbook.org), GNU TexInfo, Groff man pages
    * TeX formats: [LaTeX](http://www.latex-project.org), ConTeXt, LaTeX Beamer slides
    * PDF via LaTeX
    * Lightweight markup formats: Markdown, [reStructuredText](http://docutils.sourceforge.net/docs/ref/rst/introduction.html), [AsciiDoc](http://www.methods.co.nz/asciidoc/), [MediaWiki markup](http://www.mediawiki.org/wiki/Help:Formatting), [Emacs Org-Mode](http://orgmode.org), [Textile](http://redcloth.org/textile)

  * Converts from the following source file formats:

    * [Markdown](http://daringfireball.net/projects/markdown/) - both a "strict" markdown, as well as a Pandoc Markdown format that used many enhancements inspired by [Multimarkdown](https://github.com/fletcher/peg-multimarkdown/wiki/User's-Manual), [GitHub Flavored Markdown](http://github.github.com/github-flavored-markdown/), [PHP markdown Extra package](http://michelf.ca/projects/php-markdown/extra/) and [Maruku](http://maruku.rubyforge.org)
    * [Textile](http://redcloth.org/textile)
    * [reStructuredText](http://docutils.sourceforge.net/docs/ref/rst/introduction.html)
    * [HTML](http://www.w3.org/TR/html40/)
    * [DocBook](http://www.docbook.org)
    * [LaTeX](http://www.latex-project.org)

* [Kramdown](http://kramdown.rubyforge.org)
* [Red Carpet](https://github.com/vmg/redcarpet)
* [Maruku](http://maruku.rubyforge.org)
* [RDiscount](https://github.com/rtomayko/rdiscount)
* Many others

## Example of Various Extensions

### Inline Extensions

#### Strikethrough support

* ~~Strikethrough~~  (`~~Strikethrough~~`) Github Flavored Markdown
* <del>Strikethrough</del> (`<del>Strikethrough</del>`) HTML5 version

#### Auto-Linking

* <http://tracknut.ca> (`<http://www.auto-linking.com>`) CommonMark
* <bill@tracknut.ca> (`<bill@tracknut.ca>`) CommonMark
* <mailto:bill@tracknut.ca> (`<mailto:bill@tracknut.ca>`) CommonMark
* http://tracknut.ca (`http://www.auto-linking.com`)  GitHub Flavored Markdown
* www.tracknut.ca (`www.auto-linking.com`)  GitHub Flavored Markdown
* Note that CommonMark supports any URL scheme

#### Superscripts and Subscripts

Are not supported directly. Use \\(\LaTeX\\)/MathJax/[AsciiMath](http://asciimath.org/). For example, using \\(\LaTeX\\) delimiters:

    ```
    \\(r_t \\) \\(x^t\\) \\(y_t^2\\)
    ```
renders as  \\(r_t \\) \\(x^t\\) \\(y_t^2\\)

In order for AsciiMath to be rendered, the MathJax configuration needs to set to one that supports AsciiMath. For example `mathjaxConfig: TeX-MML-AM_CHTML`

    ```
    \` r_t \`  \` x^t \` \` y_t^2 \`
    ```
renders as  \` r_t \`  \` x^t \` \` y_t^2 \`

#### Emoji

Use the site configuration `enableEmoji = true` to enable emoji. Look on the web for emoji definitions, for example [Emojipedia](https://emojipedia.org/) [Emoji Cheatsheet](https://www.webfx.com/tools/emoji-cheat-sheet/). Here are a few examples:

| Symbol        | Emoji       |
|:-------------:|:-----------:|
|  :smile&#58;  | :smile:     |
|  :cry&#58;    | :cry:       |
|  :mask&#58;   | :mask:      |
|  :poop&#58;   | :poop:      |
| :thumbsup&#58;| :thumbsup:  |
| :smiley_cat&#58;| :smiley_cat:|


#### Footnotes

Footnotes work mostly like reference-style links. A footnote is made of two things: a marker in the text that will become a superscript number; a footnote definition that will be placed in a list of footnotes at the end of the document. A footnote looks like this:

    That's some text with a footnote.[^1]
    [^1]: And that's the footnote.

That's some text with a footnote.[^1]
[^1]: And that's the footnote.

* Footnote definitions can be found anywhere in the document, but footnotes will always be listed in the order they are linked to in the text.
* You cannot make two links to the same footnote.
* Each footnote must have a distinct name. That name will be used to link footnote references to footnote definitions, but has no effect on the numbering of the footnotes. Names can contain any character valid within an id attribute in HTML.
* Footnotes can contain block-level elements, which means that you can put multiple paragraphs, lists, blockquotes and so on in a footnote. If you want things to align better, you can leave the first line of the footnote empty and put your first paragraph just below:

        Here's text that needs another footnote.[^2]
        [^2]:
            And that's another footnote.

            That's the second paragraph.

Here's text that needs another footnote.[^2]
[^2]:
    And that's another footnote.

    That's the second paragraph.

### Definition Lists

Definition lists are made of terms and definitions of these terms, much like in a dictionary.

A simple definition list is made of a single-line term followed by a colon and the definition for that term. Terms must be separated from the previous definition by a blank line. Definitions can span on multiple lines, in which case they should be indented. But you don’t really have to: if you want to be lazy, you could forget to indent a definition that span on multiple lines and it will still work.

    Term 1
    :   Definition 1

    Term 2 with *inline markup*

    :   Definition 2

            { some code, part of Definition 2 }

        Third paragraph of definition 2.

Term 1
:   Definition 1

Term 2 with *inline markup*

:   Definition 2

        { some code, part of Definition 2 }

    Third paragraph of definition 2.

Here is another example

    Sailboat
    :    A hole in the water into which one pours money
    :    A challenging, relaxing, enjoyable world of possibilities

    Car
    :    A pollutor that just loses its value

    :    Can get you where you want to go

Sailboat
:    A hole in the water into which one pours money
:    A challenging, relaxing, enjoyable world of possibilities

Car
:    A pollutor that just loses its value

:    Can get you where you want to go

You can also associate more than one term to a definition:

    Term 1
    Term 2
    :   Definition a

    Term 3
    :   Definition b

Term 1
Term 2
:   Definition a

Term 3
:   Definition b

### Tables

The [Github-Flavored Markdown](https://github.github.com/gfm/#tables-extension-) table format is supported. [Pandoc](https://pandoc.org/MANUAL.html#extension-pipe_tables) calls these "pipe_tables":

    |     Name     |       Phone       |
    |--------------|-------------------|
    | Bill Bourne  | +1 (613) 000-1234 |
    | Sarah Bourne | +1 (123) 456-7890 |

|     Name     |       Phone       |
|--------------|-------------------|
| Bill Bourne  | +1 (613) 000-1234 |
| Sarah Bourne | +1 (123) 456-7890 |

A `:` character can be used in the delimiter row to indicate left, right, or centered justification, as the following example shows:

    | Right | Left | Default | Center |
    |------:|:-----|---------|:------:|
    |   12  |  12  |    12   |    12  |
    |  123  |  123 |   123   |   123  |
    |    1  |    1 |     1   |     1  |

| Right | Left | Default | Center |
|------:|:-----|---------|:------:|
|   12  |  12  |    12   |    12  |
|  123  |  123 |   123   |   123  |
|    1  |    1 |     1   |     1  |

Note that captions or other labels are not supported.

### Unicode Characters

Since browsers, html, and most tools are now UTF-8 compliant, using UTF-8 characters "just works". Use a [Unicode Character Table](https://unicode-table.com/en/) to search for your desired character and paste it into your markdown file. Some examples:

| Unicode |  UTF-8   | Result |            Name of Character             |
|:--------|:---------|:------:|:-----------------------------------------|
| U+2318  | E2 8C 98 | ⌘      | PLACE OF INTEREST SIGN                   |
| U+2325  | E2 8C A5 | ⌥      | OPTION KEY                               |
| U+21E7  | E2 87 A7 | ⇧      | UPWARDS WHITE ARROW (Shift)              |
| U+21EA  | E2 87 AA | ⇪      | UPWARDS WHITE ARROW FROM BAR (Caps Lock) |
| U+2303  | E2 8C 83 | ⌃      | UP ARROWHEAD (Ctrl)                      |
| U+232B  | E2 8C AB | ⌫      | ERASE TO THE LEFT (Delete)               |
| U+F8FF  | EF A3 BF |       | Apple Symbol                             |
| U+21A9  | E2 86 A9 | ↩      | LEFTWARDS ARROW WITH HOOK (Return)       |
| U+00AE  | C2 AE    | ®      | REGISTERED SIGN                          |
| U+00A9  | C2 A9    | ©      | COPYRIGHT SIGN                           |
| U+2122  | E2 84 A2 | ™      | TRADE MARK SIGN                          |
| U+2103  | E2 84 83 | ℃      | DEGREE CELSIUS                           |
| U+2109  | E2 84 89 | ℉      | DEGREE FAHRENHEIT                        |

### Using \\(\LaTeX\\) Expressions

To use \\(\LaTeX\\) and MathJax features, MathJax must be enabled. For details see the [Using ASCIIMath and MathJax]({{< ref "mathtest.md" >}}) page.

\\(\LaTeX\\) expressions can be placed between MathJax delimiters `\\( ... \\)`. This allows us to print \\\\(\LaTeX\\) symbols.

A detailed list of \\(\LaTeX\\) symbols can be found at:

* [Comprehensive \\(\LaTeX\\) Symbol List](http://tug.ctan.org/info/symbols/comprehensive/symbols-a4.pdf)
* [\\(\LaTeX\\) Symbols (From Alavaro Loustau's \\(\LaTeX\\) tutorial)](https://omega0.xyz/omega8008/Symbols.html)

### Math using MathJax

Refer to [Using ASCIIMath and MathJax]({{< ref "mathtest.md" >}}) page for details on using [MathJax](https://www.mathjax.org/) and [AsciiMath](http://asciimath.org/) in Hugo markdown. Here are two examples:

    $$R_{ab} - {\textstyle 1 \over 2}R\,g_{ab} + \Lambda\ g_{ab} = \kappa\, T_{ab}$$

renders as:

$$R_{ab} - {\textstyle 1 \over 2}R\,g_{ab} + \Lambda\ g_{ab} = \kappa\, T_{ab}$$

    $$\forall x, y : \mathbb{Z}, x > 3 \land y < 2 \Rightarrow x^2 - 2y > 5$$

renders as:

$$\forall x, y : \mathbb{Z}, x > 3 \land y < 2 \Rightarrow x^2 - 2y > 5$$
