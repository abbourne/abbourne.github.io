---
layout: page
title: Markdown Formatting
date: 2013-07-17
comments: true
sharing: true
tags: [Markdown, Pandoc]
---

# Introduction #

## Many Flavours of Markdown ##

There are many variants of Markdown formats, and each processor may support a range of extensions, and interpret the Markdown specifications in somwhat different ways. The main formats include:

* [Markdown]((http://daringfireball.net/projects/markdown/syntax)) - this is the classic orginal version
* [Multimarkdown](http://fletcher.github.com/peg-multimarkdown/mmd-manual.pdf) - the orginal extension to Markdown
* [GitHub Flavored Markdown](http://github.github.com/github-flavored-markdown/) -a small set of extension to Markdown defined by GitHub
* [Kramdown](http://kramdown.rubyforge.org/syntax.html) - extensive set of extensions based on [PHP markdown Extra package](http://michelf.ca/projects/php-markdown/extra/) and [Maruku](http://maruku.rubyforge.org)
* [Pandoc](http://johnmacfarlane.net/pandoc/README.html#pandocs-markdown) - extensive set of extensions, but strays from the original markdown syntax and extensions somewhat

## Markdown Processors ##

There are also many different Markdown processors, each with their own quirks. See the section [Other Markdown Processors and Formats] for details.

I selected [Pandoc](http://johnmacfarlane.net/pandoc) as my markdown converter, because it supports tables and a
number of advanced features, as well as the generation of pdf files via Latex, and a number of other file formats as well. I wanted to use a single processor as much as possible to avoid issues with differences in markdown syntax and features supported by different processors.

## Markdown Editing ##

* [Sublime Text 2 Notebook](st2-cheatsheet.html)
* [Table Editor Cheat Sheet](table-editor.html)

# Markdown Formatting Cheat Sheet # {#formatting-cheatsheet}

See [Pandoc Documentation](http://johnmacfarlane.net/pandoc/README.html#pandocs-markdown) for the detailed users guide for Pandoc Markdown formats and processing.

## Paragraphs ##

* A paragraph is one or more lines of text followed by one or more blank lines.
* Newlines are treated as spaces
* For a hard line break, put either two or more spaces or a backslash at the end of a line.

## Headers ##

* Pandoc requires a blank line before a header. (Markdown does not)
* Headers can contain in-line formattong, such as emphasis and links

+---------------------+---------------------+
|       Markdown      |       Result        |
+=====================+=====================+
|                     |                     |
|                     |                     |
|````                 |                     |
|A level-one header   | A level-one header  |
|==================   | ==================  |
|````                 |                     |
+---------------------+---------------------+
|                     |                     |
|                     |                     |
|````                 |                     |
| A level-two header | A level-two header |
|:-------------------|:-------------------|
| ````               |                    |
+---------------------+---------------------+

Table: Setext-style headers

+------------------------------------+----------------------------------+
|              Markdown              |              Result              |
+====================================+==================================+
| `# A level-one header #`           | # A level-one header #           |
+------------------------------------+----------------------------------+
| `## A level-two header ##`         | ## A level-two header ##         |
+------------------------------------+----------------------------------+
| `### A level-three header ###`     | ### A level-three header ###     |
+------------------------------------+----------------------------------+
| `#### A level-four header ####`    | #### A level-four header ####    |
+------------------------------------+----------------------------------+
| `##### A level-five header #####`  | ##### A level-five header #####  |
+------------------------------------+----------------------------------+
| `###### A level-six header ######` | ###### A level-six header ###### |
+------------------------------------+----------------------------------+
| `Regular Body Test`                | Regular Body Text                |
+------------------------------------+----------------------------------+

Table: Atx-Style Headers

### Header Identifiers ### {#header-identifiers}


Headers can be assigned attributes using this syntax at the end of the line containing the header text:
`{#identifier .class .class key=value key=value}`

Indentifers can be used to provide links from one section of a document to another. For example, we defined an identifer:
`# Markdown Formatting Cheat Sheet # {#formatting-cheatsheet}` so:

+---------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+
|                                        Markdown                                       |                                        Result                                       |
+=======================================================================================+=====================================================================================+
| `See the section [Markdown Formatting Cheat Sheet](#formatting-cheatsheet)`           | See the section [Markdown Formatting Cheat Sheet](#formatting-cheatsheet)           |
+---------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+
| `See the section [Markdown Formatting Cheat Sheet]`                                   | See the section [Markdown Formatting Cheat Sheet]                                   |
+---------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+
| `[See the section Markdown Formatting Cheat Sheet][Markdown Formatting Cheat Sheet]` | [See the section Markdown Formatting Cheat Sheet][Markdown Formatting Cheat Sheet] |
+---------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+


Table: Using Identifiers to link to sections within a document

The latter rows work becuase Pandoc behaves as if reference links have been defined for each header. See the section on [Links] for details of reference links

## In Line Formatting ##

| Markdown                                     | Result                                     |
|:---------------------------------------------|:-------------------------------------------|
| `_emphasis_ or *emphasis*`                   | _emphasis_ or *emphasis*                   |
| `__strong emphasis__ or **strong emphasis**` | __strong emphasis__ or **strong emphasis** |
| `~~strikeout~~`                              | ~~strikeout~~                              |
| `H~2~O - subscript`                          | H~2~O - subscript                          |
| `2^10^ - superscript`                        | 2^10^ - superscript                        |
| \`verbatim text, not formatted\`             | `verbatim text, not formatted`             |
| `Regular Body Text`                          | Regular body text                          |

Table: Basic Text Formatting

* Pandoc does not treat a \_ surrounded by alphanumeric characters as an emphasis marker. If you want to emphasise part of a work use \* instead
* A \\ will cause the following character to be treated literally
* A backslash-escaped space is parsed as a nonbreaking space
* If a verbatim text includes a backtick, use double backticks:
* The verbatim rule is that "a verbatim span starts with a string of consecutive backticks (optionally followed by a space) and ends with a string of the same number of backticks (optionally preceded by a space)."
* Attributes can be attached to verbatim text, just as with fenced code blocks: ``` ``<$>``{.haskell} ```
* Pandoc's superscripts and subscripts work for HTML output, but it fails PDF generation. I had to add `\usepackage{fixltx2e}`
to the front of my Latex template to get it to work.

* Horizontal Rules: A line containing a row of three or more *, -, or _ characters (optionally separated by spaces) produces a horizontal rule.

## Lists ##

### Bulleted and Ordered Lists ###

* A bulleted list item begins with a bullet (*, +, or -). The bullet must be followed by a space
* A list must styart with a blank line, except sub-lists.
* The "4 space rule": A list item may contain multiple paragraphs and other block-level content. However, subsequent paragraphs must be preceded by a blank line and indented four spaces or a tab. The list will look better if the first paragraph is aligned with the rest:
* List items may include other lists. In this case the preceding blank line is optional. The nested list must be indented four spaces or one tab:

+--------------------------+--------------------------+
|         Markdown         |          Result          |
+==========================+==========================+
| A simple compact list:   | A simple compact list    |
|                          |                          |
|                          | * one                    |
| ```                      | * two                    |
| * one                    | * three                  |
| * two                    |                          |
| * three                  |                          |
| ```                      |                          |
|                          |                          |
+--------------------------+--------------------------+
| A simple "loose" list,   | A simple "loose" list,   |
| with each list item      | with each list item      |
| formatted as a paragraph | formatted as a paragraph |
|                          |                          |
| ```                      | * one                    |
| * one                    |                          |
|                          | * two                    |
| * two                    |                          |
|                          | * three                  |
| * three                  |                          |
| ```                      |                          |
|                          |                          |
+--------------------------+--------------------------+
| A more complex list      | A more complex list      |
|                          |                          |
|                          | * fruits                 |
| ```                      |     - apples             |
| * fruits                 |         - macintosh      |
|     - apples             |         - red delicious  |
|         - macintosh      |     - pears              |
|         - red delicious  |     - peaches            |
|     - pears              | * vegtables              |
|     - peaches            |     - brocolli           |
| * vegtables              |     - chard              |
|     - brocolli           |                          |
|     - chard              |                          |
| ```                      |                          |
|                          |                          |
+--------------------------+--------------------------+

Table: Bullet Lists

* Ordered lists work just like bulleted lists, except that the items begin with enumerators rather than bullets.
* Enumerators are decimal numbers followed by a period and a space. The numbers themselves are ignored. (Standard Masrkdown)
* Fancy Lists: Ordered list items to be marked with uppercase and lowercase letters and roman numerals, in addition to arabic numerals. List markers may be enclosed in parentheses or followed by a single right-parentheses or period. They must be separated from the text that follows by at least one space, and, if the list marker is a capital letter with a period, by at least two spaces (Pandoc Extension)
* Startnum: Pandoc also pays attention to the type of list marker used, and to the starting number, and both of these are preserved where possible in the output format. (Pandoc Extension)

+------------------------+----------------------+
|        Markdown        |        Result        |
+========================+======================+
|                        |                      |
|                        |                      |
| ```                    | 1.  one              |
| 1.  one                | 7.  two              |
| 7.  two                | 4.  three            |
| 4.  three              |                      |
| ```                    |                      |
+------------------------+----------------------+
| This is a fancy list   | This is a fancy list |
| with starting numbers. | with starting numbers|
|                        |                      |
| ```                    |  9) Ninth            |
|  9)  Ninth             | 10)  Tenth           |
| 10)  Tenth             | 11)  Eleventh        |
| 11)  Eleventh          |      ii. subone      |
|      ii. subone        |     iii. subtwo      |
|     iii. subtwo        |      iv. subthree    |
|      iv. subthree      |                      |
| ```                    |                      |
+------------------------+----------------------+

Table: Ordered Lists

### Definition Lists ###

* Each term must fit on one line, which may optionally be followed by a blank line, and must be followed by one or more definitions.
* A definition begins with a colon or tilde, which may be indented one or two spaces.
* The body of the definition (including the first line, aside from the colon or tilde) should be indented four spaces. A term may have multiple definitions, and each definition may consist of one or more block elements (paragraph, code block, list, etc.), each indented four spaces or one tab stop.
* If you leave space after the definition, the blocks of the definitions will be considered paragraphs.
* For a compact definition list, do not leave space between the definition and the next term:

+----------------------------------------------------------------+----------------------------------------------------------------+
|                            Markdown                            |                             Result                             |
+================================================================+================================================================+
| This is an example of a definition list                        | This is an example of a definition list                        |
|                                                                |                                                                |
| ```                                                            | Term 1                                                         |
| Term 1                                                         |                                                                |
|                                                                | :   Definition 1                                               |
| :   Definition 1                                               |                                                                |
|                                                                | Term 2 with *inline markup*                                    |
| Term 2 with *inline markup*                                    |                                                                |
|                                                                | :   Definition 2                                               |
| :   Definition 2                                               |                                                                |
|                                                                |         { some code, part of Definition 2 }                    |
|         { some code, part of Definition 2 }                    |                                                                |
|                                                                |     Third paragraph of definition 2.                           |
|     Third paragraph of definition 2.                           |                                                                |
| ```                                                            |                                                                |
+----------------------------------------------------------------+----------------------------------------------------------------+
| ```                                                            | Here is another example, to show the formatting                |
| Here is another example, to show the formatting                |                                                                |
|                                                                | Sailboat                                                       |
| Sailboat                                                       | :    A hole in the water into which one pours money            |
| :    A hole in the water into which one pours money            | :    A challenging, relaxing, enjoyable world of possibilities |
| :    A challenging, relaxing, enjoyable world of possibilities | Car                                                            |
| Car                                                            | :    A pollutor that just loses its value                      |
| :    A pollutor that just loses its value                      |                                                                |
|                                                                | :    Can get you where you want to go                          |
| :    Can get you where you want to go                          |                                                                |
| ```                                                            |                                                                |
|                                                                |                                                                |
+----------------------------------------------------------------+----------------------------------------------------------------+

Table: Definition Lists

### Numbered Example Lists ###

* The special list marker @ can be used for sequentially numbered examples throughout a whole document
* The first list item with a @ marker will be numbered ‘1’, the next ‘2’, and so on.
* Numbered examples can be labeled with any alphanumber string and referred to elsewhere in the document

+--------------------------------------------------+--------------------------------------------------+
|                     Markdown                     |                      Result                      |
+==================================================+==================================================+
| ```                                              | (@1st)  My first example will be numbered (1).   |
| (@1st)  My first example will be numbered (1).   |                                                  |
|                                                  | some stuff here.                                 |
| some stuff here                                  |                                                  |
|                                                  | (@2nd)  My second example will be numbered (2).  |
| (@2nd)  My second example will be numbered (2).  |                                                  |
|                                                  | and some more stuff here.                        |
| and some more stuff here.                        |                                                  |
|                                                  | (@3rd)  My third example will be numbered (3).   |
| (@3rd)  My third example will be numbered (3).   |                                                  |
|                                                  | As (@1st) illustrates, its different from (@3rd) |
| As (@1st) illustrates, its different from (@3rd) |                                                  |
| ```                                              |                                                  |
+--------------------------------------------------+--------------------------------------------------+

Table: Numbered Example Lists

### List Quirks and Gotchas ###

* Consider the example:

    ```
    +   First
    +   Second:
        -   Fee
        -   Fie
        -   Foe

    +   Third
    ```

    * Pandoc follows a simple rule: if the text is followed by a blank line, it is treated as a paragraph. Since “Second” is followed by a list, and not a blank line, it isn’t treated as a paragraph. The fact that the list is followed by a blank line is irrelevant.

* If you need to explicitly end a list, put in an html comment:

    ```
    -   item one
    -   item two
    
    <!-- end of list -->
    
        { my code block }
    ```

    ```
    1.  one
    2.  two
    3.  three
    
    <!-- end of list -->
    
    1.  uno
    2.  dos
    3.  tres
    ```

## Block Quotes ##

A block quotation is one or more paragraphs or other block elements (such as lists or headers), with each line preceded by a > character and an optional space. (The > need not start at the left margin, but it should not be indented more than three spaces.)

```
> This is a block quote. This
> paragraph has two lines.
>
> 1. This is a list inside a block quote.
> 2. Second item.
```

> This is a block quote. This
> paragraph has two lines.
>
> 1. This is a list inside a block quote.
> 2. Second item.

Among the block elements that can be contained in a block quote are other block quotes. That is, block quotes can be nested:

```
> This is a block quote.
>
> > A block quote within a block quote.
```

> This is a block quote.
>
> > A block quote within a block quote.

If the > character is followed by an optional space, that space will be considered part of the block quote marker and not part of the indentation of the contents. Thus, to put an indented code block in a block quote, you need five spaces after the >:

```
> Indented Text:
>     This is some code
```

> Indented Text:
>
>     This text is indented


## Links ## {#links}

### Auto-Linking ###

* If you enclose a URL or email address in pointy brackets, it will become a link:

| Markdown               | Result               |
|:-----------------------|:---------------------|
| `<http://google.com>`  | <http://google.com>  |
| `<sam@green.eggs.ham>` | <sam@green.eggs.ham> |

Table: Automatic Links

### In-Line Links ###

* An inline link consists of the link text in square brackets, followed by the URL in parentheses.
* Optionally, the URL can be followed by a link title, in quotes. But in the example below, when I try to put a libk title in quotes within a table,
  Pandoc generates the HTML fint, but it fails when tryiong to generate a PDF file from the Latex output.
* The link text can contain formatting (such as emphasis)

| Markdown                      | Result                      |
|:------------------------------|:----------------------------|
| `[Google](http://google.com)` | [Google](http://google.com) |
| `[_FSF_](http://fsf.org)`     | [_FSF_](http://fsf.org)     |


Table: In-Line Links

### Reference Links ###

* An _explicit_ reference link has two parts, the link itself and the link definition, which may occur elsewhere in the document (either before or after the link).
* The link itself consists of link text in square brackets, followed by a label in square brackets.
* The link definition consists of the bracketed label, followed by a colon and a space, followed by the URL, and optionally (after a space) a link title either in quotes or in parentheses.
* Note that link labels are not case sensitive
* Sample link definitions:

    ```
    [my label 1]: http://google.com  "My title, optional"
    [my label 2]: /foo
    [my label 3]: http://fsf.org (The free software foundation)
    [my label 4]: /bar#special  'A title in single quotes'
    [my label 5]: <http://foo.bar.baz>
    ```

[my label 1]: http://google.com  "My title, optional"
[my label 2]: /foo
[my label 3]: http://fsf.org "The free software foundation"
[my label 4]: /bar#special  "A title in single quotes"
[my label 5]: <http://foo.bar.baz>


| Markdown Reference Links | Result               |
|:-------------------------|:---------------------|
| `[FSF][my label 3]`      | [FSF][my label 3]    |
| `[Google][my label 1]`   | [Google][my label 1] |
| `[my label 1]`           | [my label 1]         |
| `[my label 3][]`         | [my label 3][]       |

Table: Reference Link Usage (Explicit and Implicit)

### Internal Links ###

* See the section [Header Identifiers](#header-identifiers) for how to create links to other sections of the same document

### Footnotes ###

* The identifiers in footnote references may not contain spaces, tabs, or newlines
* The identifiers are used only to correlate the footnote reference with the note itself; in the output, footnotes will be numbered sequentially.
* The footnotes themselves need not be placed at the end of the document. They may appear anywhere except inside other block elements (lists, block quotes, tables, etc.).
* The example in the Pandoc User Guide whichb includes an indented code block of the form `{ some.code }` generates HTML OK, but but it fails when tryiong to generate a PDF file from the Latex output.
* Sample footnaotes syntax:

    ```
    Here is a footnote reference,[^1] and another.[^longnote]
    
    [^1]: Here is the footnote.
    
    [^longnote]: Here's one with multiple blocks.
    
        Subsequent paragraphs are indented to show that they
    belong to the previous footnote.
    
        The whole paragraph can be indented, or just the first
        line.  In this way, multi-paragraph footnotes work like
        multi-paragraph list items.
    
    This paragraph won't be part of the note, because it
    isn't indented.
    ```
* results in:

Here is a footnote reference,[^1] and another.[^longnote]

[^1]: Here is the footnote.

[^longnote]: Here's one with multiple blocks.

    Subsequent paragraphs are indented to show that they
belong to the previous footnote.

    The whole paragraph can be indented, or just the first
    line.  In this way, multi-paragraph footnotes work like
    multi-paragraph list items.

This paragraph won't be part of the note, because it
isn't indented.

* Inline footnotes are also allowed (though, unlike regular notes, they cannot contain multiple paragraphs). The syntax is as follows:

    ```
    Here is an inline note.^[Inlines notes are easier to write, since
    you don't have to pick an identifier and move down to type the
    note.]
    ```
Here is an inline note.^[Inlines notes are easier to write, since
you don't have to pick an identifier and move down to type the
note.]

## Images ##

* A link immediately preceded by a ! will be treated as an image. The link text will be used as the image’s alt text
* When processing the example text, Pandoc generates the HTML, but fails when generating the PDF from Latex if the link includes any link text.
* An image occurring by itself in a paragraph will be rendered as a figure with a caption.
* You have to be careful about where you place your images. The generated html makes a URL from the image location, but the generated Latex needs a directory path to the image. This can cause the PDF generation to fail. My solution to this problem is to:
    * Only use images that are the same directory as the markdown source file, or a subdirectory.
    * cd to the directory the markdown source is in before calling pandoc
    * Enter the image file location as relative to the directory the markdown source file is in
* In the PDF output, latex will use any pixels/inch sizing information in the image to size it accurately for the page (you can't enter width and height information in the markdown like you can in html). So make sure the sizing information is included in the image so its gets formatted properly for the pdf page.

`![My Logo](bicycle-icon3-114x114.png)`

![My Logo](bicycle-icon3-114x114.png "Bills signed bicycle logo")

* If you just want a regular inline image, just make sure it is not the only thing in the paragraph. One way to do this is to insert a nonbreaking space after the image.

`This is the Sublime Text Icon ![Sublime Text](sublime_text.png) here.`

This is the Sublime Text Icon ![Sublime Text](sublime_text.png "Sublime Text Cheat Sheet Logo") is here.

## Tables ##

Since I use [Sublime Text 2](http://www.sublimetext.com) for text editing, I make use of the excellent
[Table Editor](https://github.com/vkocubinsky/SublimeTableEditor) package. This means I need to use table formats that are supported by both Pandoc and Table Editor.

Refer to the [Table Editor Cheat Sheet](table-editor.html) for the Table Editor commands.

### Table Types ###

+-----------------------+---------------+-------------------------------------------------------------------------------+
|         Pandoc        |  Table Editor |                                     Notes                                     |
+=======================+===============+===============================================================================+
| Pipe                  | Simple Table  | Column alignment is not supprted by Pandoc                                    |
+-----------------------+---------------+-------------------------------------------------------------------------------+
| Pipe                  | Pandoc        | Column alignment is not supprted by Pandoc                                    |
+-----------------------+---------------+-------------------------------------------------------------------------------+
| Pipe - emacs org mode | EmacsOrgMode  | Column alignment is not supprted by Pandoc                                    |
+-----------------------+---------------+-------------------------------------------------------------------------------+
| Pipe                  | Markdown      | Use : on header row to indicate column alinment.                              |
|                       |               | The cells of pipe tables cannot contain block elements                        |
|                       |               | like paragraphs and lists, and cannot span multiple lines.                    |
|                       |               | The syntax is the same as                                                     |
|                       |               | in [PHP markdown extra](http://michelf.ca/projects/php-markdown/extra/#table) |
+-----------------------+---------------+-------------------------------------------------------------------------------+
| Grid                  | No name       | Table editor supports this form of table but                                  |
|                       |               | does not give it a name. Pandoc does not support                              |
|                       |               | alignments , or cells that span multiple columns or rows.                     |
|                       |               | The cells of grid tables may contain arbitrary block                          |
|                       |               | elements (multiple paragraphs, code blocks, lists, etc.)                      |
+-----------------------+---------------+-------------------------------------------------------------------------------+
| Simple Table,         | Not Supported | These tables are not supported at all by                                      |
| Multi-Line Table      |               | the table editor                                                              |
+-----------------------+---------------+-------------------------------------------------------------------------------+

### Simple Table (Table Editor Definition)  ###

The Sublime Text 2 [Table Editor Plugin's](https://github.com/vkocubinsky/SublimeTableEditor#readme) simple table looks like the following.
[Pandoc](http://johnmacfarlane.net/pandoc/README.html#tables) supports this form:

```
| Name         |             Phone |
|:-------------|------------------:|
| Bill Bourne  | +1 (613) 555-1234 |
| Sarah Bourne | +1 (617) 555-1234 |
```

| Name         |             Phone |
|:-------------|------------------:|
| Bill Bourne  | +1 (613) 555-1234 |
| Sarah Bourne | +1 (617) 555-1234 |

Table: This is a Simple Table

### Pandoc Table (aka Grid Table) ###

ST2's [Table Editor Plugin's](https://github.com/vkocubinsky/SublimeTableEditor#readme) Pandoc table looks like the following.
[Pandoc](http://johnmacfarlane.net/pandoc/README.html#tables) supports this form, but justification is not supported.

```
+--------------+---------------+
| First Header | Second Header |
+==============+===============+
| Content Cell | Content Cell  |
+--------------+---------------+
| Content Cell | Content Cell  |
+--------------+---------------+
| Another Cell | Last Cell     |
+--------------+---------------+
```

+--------------+---------------+
| First Header | Second Header |
+==============+===============+
| Content Cell | Content Cell  |
+--------------+---------------+
| Content Cell | Content Cell  |
+--------------+---------------+
| Another Cell | Last Cell     |
+--------------+---------------+

Table: This is a Pandoc Table

# Unicode Characters #

Pandoc renders Unicode characters properly in HTML, but not in PDF. I have not figured out what the issue is yet.

+---------+----------+--------+------------------------------------------+
| Unicode |  UTF-8   | Result |            Name of Character             |
+=========+==========+========+==========================================+
| U+2318  | E2 8C 98 | ⌘      | PLACE OF INTEREST SIGN                   |
+---------+----------+--------+------------------------------------------+
| U+2325  | E2 8C A5 | ⌥      | OPTION KEY                               |
+---------+----------+--------+------------------------------------------+
| U+21E7  | E2 87 A7 | ⇧      | UPWARDS WHITE ARROW (Shift)              |
+---------+----------+--------+------------------------------------------+
| U+21EA  | E2 87 AA | ⇪      | UPWARDS WHITE ARROW FROM BAR (Caps Lock) |
+---------+----------+--------+------------------------------------------+
| U+2303  | E2 8C 83 | ⌃      | UP ARROWHEAD (Ctrl)                      |
+---------+----------+--------+------------------------------------------+
| U+232B  | E2 8C AB | ⌫      | ERASE TO THE LEFT (Delete)               |
+---------+----------+--------+------------------------------------------+
| U+F8FF  | EF A3 BF |       | Apple Symbol                             |
+---------+----------+--------+------------------------------------------+
| U+21A9  | E2 86 A9 | ↩      | LEFTWARDS ARROW WITH HOOK (Return)       |
+---------+----------+--------+------------------------------------------+
| U+00AE  | C2 AE    | ®      | REGISTERED SIGN                          |
+---------+----------+--------+------------------------------------------+
| U+00A9  | C2 A9    | ©      | COPYRIGHT SIGN                           |
+---------+----------+--------+------------------------------------------+
| U+2122  | E2 84 A2 | ™      | TRADE MARK SIGN                          |
+---------+----------+--------+------------------------------------------+
| U+2103  | E2 84 83 | ℃      | DEGREE CELSIUS                           |
+---------+----------+--------+------------------------------------------+
| U+2109  | E2 84 89 | ℉      | DEGREE FAHRENHEIT                        |
+---------+----------+--------+------------------------------------------+


# Inlining of Native Output Code #

## Using TeX Expressions ##

$\TeX$ expressions can be placed between dollar signs - eg. `$\TeX$`. This allows us to print $\TeX$ symbols.

A detailed list of $\TeX$ symbols can be found at:

* [Comprehensive $\LaTeX$ Symbol List](http://www.tex.ac.uk/tex-archive/info/symbols/comprehensive/symbols-a4.pdf)
* [$\LaTeX$ Symbols (From Alavaro Loustau's $\LaTeX$ tutorial)](http://omega.albany.edu:8008/Symbols.html)

Useful Symbols:

* `\textcopyright`

## Math using MathJax ##

Pandoc supports typsetting math for HTML output using a number of different mechanisms.
The one I am using here is [MathJax](http://www.mathjax.org). I'm using $\LaTeX$ Math, since Pandoc supports it in multiple output formats.

The following code:

```
$$R_{ab} - {\textstyle 1 \over 2}R\,g_{ab} + \Lambda\ g_{ab} = \kappa\, T_{ab}$$
$$\forall x, y : \mathbb{Z}, x > 3 \land y < 2 \Rightarrow x^2 - 2y > 5$$
$$fac(n) = \prod_{j=1}^{n}j , n \in \mathbb{NW$$
```
Renders as:

$$R_{ab} - {\textstyle 1 \over 2}R\,g_{ab} + \Lambda\ g_{ab} = \kappa\, T_{ab}$$
$$\forall x, y : \mathbb{Z}, x > 3 \land y < 2 \Rightarrow x^2 - 2y > 5$$
$$fac(n) = \prod_{j=1}^{n}j , n \in \mathbb{W}$$

Here's some information on $\LaTeX$ Math:

* [Host Math Online Editor](http://www.hostmath.com/) - supports $\LaTeX\ $, \$TeX\ $, AMSmath or ASCIIMath notation
* [codecogs Online Latex Math Editor](https://www.codecogs.com/latex/eqneditor.php)
* [American Mathematical Society Short Math Guide for Latex](ftp://ftp.ams.org/pub/tex/doc/amsmath/short-math-guide.pdf)
* [sharelatex Mathematical Expressions Guide](https://www.sharelatex.com/learn/Mathematical_expressions)
* [WikiBooks Latex Mathematics](https://en.wikibooks.org/wiki/LaTeX/Mathematics)
* [Art of Problem Solving Latex Wiki - Symbols](https://www.artofproblemsolving.com/wiki/index.php?title=LaTeX:Symbols)
* [The Student Room Wiki - Latex](http://www.thestudentroom.co.uk/wiki/LaTex)

# Other Markdown Processors and Formats #  {#processors}

There are many flavours of [Markdown](http://daringfireball.net/projects/markdown/syntax), each with its own
characteristics. My requirements included the ability to support tables, and the ability to generate PDF files as well
as html.

Major Markdown processors, and the variants of Markdown they support include:

* [Pandoc](http://johnmacfarlane.net/pandoc)

    * Supported by OctoPress & Jekyll via a Jekyll plug-in [Jekyll Pandoc Plugin](https://github.com/dsanson/jekyll-pandoc-plugin)
    * Written in Haskell. May be slow for large sites
    * Supports an enhanced Markdown inspired by, but not identical to, markdown extensions in PHP markdown Extra package](http://michelf.ca/projects/php-markdown/extra/) and [Maruku](http://maruku.rubyforge.org)

    * Converts to many file formats:

        * XHTML, HTML5, and HTML slide shows
        * Microsoft Word docx, OpenOffice/LibreOffice ODT, OpenDocument XML
        * EPUB, [DocBook](http://www.docbook.org), GNU TexInfo, Groff man pages
        * TeX formats: [LaTeX](http://www.latex-project.org), ConTeXt, LaTeX Beamer slides
        * PDF via LaTeX
        * Lightweight markup formats: Markdown, [reStructuredText](http://docutils.sourceforge.net/docs/ref/rst/introduction.html), [AsciiDoc](http://www.methods.co.nz/asciidoc/), [MediaWiki markup](http://www.mediawiki.org/wiki/Help:Formatting), [Emacs Org-Mode](http://orgmode.org), [Textile](http://redcloth.org/textile)

    * Converts from the following source file formats:

        * [Markdown](http://daringfireball.net/projects/markdown/) - both a "strict" markdown, as well as a Pandoc Markdown format that used many enhancements inspired by [Multimarkdown](https://github.com/fletcher/peg-multimarkdown/wiki/User's-Manual), [GitHub Flavored Markdown](http://github.github.com/github-flavored-markdown/), PHP markdown Extra package](http://michelf.ca/projects/php-markdown/extra/) and [Maruku](http://maruku.rubyforge.org)
        * [Textile](http://redcloth.org/textile)
        * [reStructuredText](http://docutils.sourceforge.net/docs/ref/rst/introduction.html)
        * [HTML](http://www.w3.org/TR/html40/)
        * [DocBook](http://www.docbook.org)
        * [LaTeX](http://www.latex-project.org)

    * Considered the "swiss army knife" of documents conversation, given the large number of formats, and the large number of conversion and formatting options it supports.

* [Kramdown](http://kramdown.rubyforge.org)

    * Supported in OctoPress
    * Fast Ruby implementation
    * Supports Markdown plus extensions made popular by the [PHP markdown Extra package](http://michelf.ca/projects/php-markdown/extra/) and [Maruku](http://maruku.rubyforge.org)

* [Red Carpet](https://github.com/vmg/redcarpet)

    * Supported by OctoPress and Jekyll
    * Is the markdown processor used by GitHub
    * Supports [GitHub Flavored Markdown](http://github.github.com/github-flavored-markdown/)

* [Maruku](http://maruku.rubyforge.org)

    * Supported by OctoPress and Jekyll
    * Supports an extended version of Markdown.

* [RDiscount](https://github.com/rtomayko/rdiscount)

    * Supported by OctoPress and Jekyll
    * A Ruby wrapper on the Discount Markdown processor written in C
    * Supposed to be very fast
