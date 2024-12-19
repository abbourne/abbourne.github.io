---
title: "Using ASCIIMath and MathJax"
categories: ["Playground"]
tags: [Markdown, Pandoc]
mathjax: true
draft: false
---

This page tests and documents using MathJax, Latex and AsciiMath with Hugo and markdown.

## Getting a Markdown Processor to Ignore Markup

MathJax, AsciiMath, and similar processors use special markup characters in the the html file. Often these characters overlap with markdown's markup, and the markdown processor will mess things up. There are a number of options:

* Use the `\` backslash, which is markdown's escape character, to escape characters that would be processed by markdown. See [Escaping Characters in markdown](https://www.markdownguide.org/basic-syntax/#escaping-characters)

* Create a simple hugo shortcode which does nothing but pass through text verbatim, bypassing the markdown processor. Here's an example of AsciiMath using the `in` (for inline) shortcode:

  ```markdown
  {{</*in>}}` r_t = l_t - (2 * l_s)/(2pi) `{{</in*/>}}
  ```

  * renders as {{<in>}}`sum_(i=1)^n i^3=((n(n+1))/2)^2`{{</in>}} inline.
  * By the way, to make this example, I had resort to using `/* */` to comment out the shortcode invocation in order to display this example. See [Escaping Hugo Shortcodes](https://www.ii.com/hugo-tips-fragments/#_escaping_hugo_shortcodes) for for more details on this, and other tricks to prevent markup from getting executed.

## [AsciiMath](http://asciimath.org/)

[AsciiMath](http://asciimath.org/) is rendered by the [MathJAX](https://www.mathjax.org/) libraries.
By default, AsciiMath uses a "backtick" as it's delimiter, and it only supports inline rendering.
Note that backticks used in the html web page that also renders AsciiMath may mess up the rendering, as AsciiMath will see it as the delimiter of an equation... be careful

### Examples

1. Use backticks and raw AsciiMath. The following

    ```markdown
    \` r_t = l_t - (2 * l_s)/(2pi) \`
    ```

    * renders as \` r_t = l_t - (2 * l_s)/(2pi) \` inline.

2. Or you can use the `in` shortcode:

    ```markdown
    {{</*in>}}`sum_(i=1)^n i^3=((n(n+1))/2)^2`{{</in*/>}}
    ```

    * renders as {{<in>}}`sum_(i=1)^n i^3=((n(n+1))/2)^2`{{</in>}} inline.

3. Create an inline `am` shortcode:

    ```markdown
    {{</*am math="sum_(i=1)^n i^3=((n(n+1))/2)^2"*/>}}
    ```

    * renders as {{<am math="sum_(i=1)^n i^3=((n(n+1))/2)^2">}} inline

4. Create a block `AsciiMath` shortcode.

    ```markdown
    {{</* AsciiMath math="r_c = r_t - (sin(theta_l) * h_c)" comment="This is a comment" caption="This is a caption" */>}}
    ```

    * renders as:

    {{< AsciiMath math="r_c = r_t - (sin(theta_l) * h_c)" comment="This is a comment" caption="This is a caption" >}}

    * Note that the shortcode takes an optional comment and caption.

## \\(\LaTeX \\) and [MathJax](https://www.mathjax.org/)

See the [MathJax documentation](http://docs.mathjax.org/en/latest/) for details.

By default, the MathJax TeX processor uses the LaTeX math delimiters, which are `\(...\)` for in-line math, and `\[...\]` for displayed equations. It also recognizes the TeX delimiters `$$...$$` for displayed equations.

### Examples

1. Inline math example:

    ```markdown
    \\( x = \frac{-b \pm \sqrt{c^2 - 4ac}}{2a} \\)
    ```

    * Renders as \\( x = \frac{-b \pm \sqrt{c^2 - 4ac}}{2a} \\). Note when \\(a \ne 0\\), there are two solutions to \\(ax^2 + bx + c = 0\\)
    * You could also use the `in` shortcode as above.

2. Create an `mj` shortcode:

    ```markdown
    {{</*mj math="x = \frac{-b \pm \sqrt{c^2 - 4ac}}{2a}"*/>}}
    ```

    * renders as  {{<mj math="x = \frac{-b \pm \sqrt{c^2 - 4ac}}{2a}">}}

3. Block example:

    ```markdown
    \\[ \sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6} \\]
    ```

    * Renders as:
    \\[ \sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6} \\] .

4. Create a `MathJax` shortcode

    ```markdown
    {{</*MathJax math="\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}" caption="This is a caption"*/>}}
    ```

    * Renders as:
    {{<MathJax math="\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}" caption="This is a caption">}}

## \\(\LaTeX\\) Rendering

Since MathJax uses \\(\LaTeX\\), the same delimiters may be used to render any Latex markup.

* [Comprehensive \\(\LaTeX \\) Symbol List](http://tug.ctan.org/info/symbols/comprehensive/symbols-a4.pdf)
* [\\(\LaTeX\\) Symbols (From Alavaro Loustau's \\(\LaTeX\\) tutorial)](https://omega0.xyz/omega8008/Symbols.html)
