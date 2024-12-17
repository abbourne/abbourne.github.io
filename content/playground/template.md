---
title: "Template for a Post article" # also placed in pages <head> for SEO
lead: "You need this knowledge to avoid being stranded on the road" # Mainroad theme - subtitle
description: "" # placed in <head> tag for SEO
summary: "This is a summary" #If exists, is used as the summary text in lists. 
keywords: [ "cycling", "bikes", "education", "tires", "maintenance"] # placed in <head> tag for SEO
categories: ["Cycling Safety"] #Mainroad Theme parameter
tags: ["Equipment"] #Mainroad theme parameter
date: "2022-12-31"
modified: "2024-12-16" # sets lastmod date, determines list ordering. Overridden if enableGitInfo = true
thumbnail: "/img/hugo-logo-235px.png"  #an image that looks good when display 200px on a side
postthumbvisible: true #Set to false to remove the thumbnail from the post heading
listthumbvisible: true #set to false to remove the thumbnail from the list entry
draft: false  #set to true to keep article from being published unless --builtdrafts flag is passed
---

And introductory paragraph goes here, **without a title**.
If the more comment if used, the text above the more is used as a summary, and any summary tag in the frot matter is ignored.
<!--more-->
Text below the more will not be included in the summary.

# Markdown in Hugo

## Introduction

This article is a reference for Hugo's version of markdown as well as Hugo's processing.
Here are a few good Markdown references and tutorials:

General markdown references:

* [Markdown Guide](https://www.markdownguide.org/)
* [Wikipedia Markdown entry](https://en.wikipedia.org/wiki/Markdown)
* [CommonMark](https://commonmark.org/) - the markdown "standard"

All about Hugo's markdown:

* [Goldmark](https://github.com/yuin/goldmark) - Goldmark is a markdown processor written in go, which is used by Hugo
* [Configuring Hugo's markdown](https://gohugo.io/getting-started/configuration-markup/#goldmark) - specific information on configuring Goldmark, and what Goldmark features Hugo supports.
* [Image Processing](https://gohugo.io/content-management/image-processing/)
* [Shortcodes](https://gohugo.io/content-management/shortcodes/)
* [Links and Cross References](https://gohugo.io/content-management/cross-references/)
* [Markdown Attributes](https://gohugo.io/content-management/markdown-attributes/) - add HTML attributes when rendering HTML
* [Syntax Hightlighting](https://gohugo.io/content-management/syntax-highlighting/)
* [Diagrams](https://gohugo.io/content-management/diagrams/)
* [Mathematics](https://gohugo.io/content-management/mathematics/) - Note that many themes implement their own support. [Mainroad](https://github.com/Vimux/Mainroad) does.
* Emoji Support. Set `enableEmoji` to `true` in the [main site configuration](https://gohugo.io/getting-started/configuration/#all-configuration-settings). For a list of emoji see [Emoji Cheat Sheet](https://www.webfx.com/tools/emoji-cheat-sheet/)

# Headings (Heading 1)

start here

## Heading 2

next paragraph

### Heading 3

next paragraph

#### Heading 4

next paragraph

##### Heading 5

next paragraph

###### Heading 6

and we are done!

# List Types

Unordered list:

* First item
* Second item
* Third item
* Last item

Ordered List:

1. First item
2. Second item
3. Third item
4. Last item

Definition List [Markdown Extra](https://michelf.ca/projects/php-markdown/extra/#def-list):

Apple
:   Pomaceous fruit of plants of the genus Malus in 
    the family Rosaceae.
:   Also a computer company

Orange
:   The fruit of an evergreen tree of the genus Citrus.

Peanut
:   Actually a legume, not a nut at all!

Task List [GitHub Flavored Markdown](https://github.github.com/gfm/#task-list-items-extension-):

* [ ] Foo to do
* [ ] Baz to do
* [x] Baz is done

Lists can be nested:

* Item 1
* Item 2
    * Another iten
    * another item
        1. sub-item 1
        2. sub item 2
        3. sub item 3
    * final item

# Blockquotes

> ### Blockquotes can have a title
> This is a _simple_ blockquote.
>> Block quotes can be nested

Basic admonitions:

> [!NOTE]
> Useful information that users should know, even when skimming content.

> [!TIP]
> Helpful advice for doing things better or more easily.

> [!IMPORTANT]
> Key information users need to know to achieve their goal.

> [!WARNING]
> Urgent info that needs immediate user attention to avoid problems.

> [!CAUTION]
> Advises about risks or negative outcomes of certain actions.

# Tables

# Code

# Math

# Inline Elements

## Emoji

Use the site configuration `enableEmoji = true` to enable emoji. Look on the web for emoji definitions, for example [Emojipedia](https://emojipedia.org/) [Emoji Cheatsheet](https://www.webfx.com/tools/emoji-cheat-sheet/). Here are a few examples:

| Symbol        | Emoji       |
|:-------------:|:-----------:|
|  :smile&#58;  | :smile:     |
|  :cry&#58;    | :cry:       |
|  :mask&#58;   | :mask:      |
|  :poop&#58;   | :poop:      |
| :thumbsup&#58;| :thumbsup:  |
| :smiley_cat&#58;| :smiley_cat:|

## Unicode Characters

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

## Footnotes



