---
title: Hugo Markdown Image Handling
date: 2022-12-17
Description: The article discusses the details of how Goldmark Markdown and Hugo handles images, along with how to add attributes such a positioning and sizing when using images in a Hugo Markdown file.
summary: The article discusses the details of how Goldmark Markdown and Hugo handles images, along with how to add attributes such a positioning and sizing when using images in a Hugo Markdown file.
tags: [Markdown, Pandoc, Hugo]
categories: [Technology]
thumbnail: "/img/hugo-logo-200px.png"
thumbvisible: false
draft: false
---

The article discusses the details of how Goldmark Markdown and Hugo handles images, along with how to add attributes such a positioning and sizing when using images in a Hugo Markdown file.

## Introduction

For general  Markdown references and tutorials see:

* [Goldmark](https://github.com/yuin/goldmark) - Goldmark is a markdown processor written in go, which is used by Hugo
* [Configuring Hugo's Markdown](https://gohugo.io/getting-started/configuration-markup/) lists all the configuration options for Hugo's Goldmark settings.
* [Markdown Guide](https://www.markdownguide.org/)
* [Wikipedia Markdown entry](https://en.wikipedia.org/wiki/Markdown)
* [CommonMark](https://commonmark.org/) - the markdown "standard"

## Image Handling

There are three ways to use images in Hugo:

1. Use the standard [Markdown Image Tag](https://www.markdownguide.org/basic-syntax/#images-1).  Markdown has very basic support for images.
2. Use Hugo's [figure shortcode](https://gohugo.io/content-management/shortcodes/#figure). Hugo supplies a shortcode to pu an image in an [HTML5 `<figure>` element](https://html5doctor.com/the-figure-figcaption-elements/). It includes a number of parameters.
3. Use HTML within the Markdown file
4. OK... the third way is to di something custom. For example create your own custom shortcode, use [Hugo Render Hooks](https://gohugo.io/templates/render-hooks/), or use a different external Markdown processor like [Pandoc](https://pandoc.org/)

## Using the Markdown Image tag

The Markdown Image tag is of the form `![alt text](imageURL "Optional Title")`. It will render the image inline. For  example, `![The Hugo Logo](./hugo-logo-125px.png "The Hugo Mascot")` render as ![The Hugo Logo](./hugo-logo-125px.png "The Hugo Mascot"). There are no options to set the image size or any other properties (At least in the default usage). The HTML generated is ` Markdown generates `<img src="./hugo-logo-125px.png" alt="The Hugo Logo" title="The Hugo Mascot">`. And the in line image will determine the height of the line it is on.

If the image tag is put on a separate line, as if it was a new paragraph, it will be treated as new paragraph. So:

```
![The Hugo Logo](./hugo-logo-125px.png "The Hugo Mascot")
```

The image will be rendered within it's own `<p></p>` paragraph block:

![The Hugo Logo](./hugo-logo-125px.png "The Hugo Mascot")

The HTML generated is `<p><img src="./hugo-logo-125px.png" alt="The Hugo Logo" title="The Hugo Mascot"></p>`
So, the CommonMark-specification is to generate an HTML `<img>` tag without an HTML5 `<figure>,</figure>` - a markdown image is an _inline_, not a block element. For Markdown, this means that:

* If you put an image on its own (not _inlined_) in another paragraph), it would be wrapped in `<p></p>` tags. (Even if you provide your own a [Hugo Render Hook Template](https://gohugo.io/templates/render-hooks/) )
* Hugo/Goldmark has [custom attribute support](https://gohugo.io/getting-started/configuration-markup/#goldmark) that allows attributes to be placed on block elements, but _not_ inline elements. So:

    ```
    ## My Title Has Attributes {class="myclass}   - This is OK

    ![The Hugo Logo](./hugo-logo-125px.png) {height=100px, class="right}  - This wont work!
    ```

In Hugo [Hugo Release v0.108.8](https://github.com/gohugoio/hugo/releases/tag/v0.108.0), there is now a workaround for this:

Set `markup.goldmark.parser.wrapStandAloneImageWithinParagraph = false` so standalone images will not be wrapped in `<p>>/p>` tags. Also set `block = true` to support attributes on block elements:

```
[markup]
  [markup.goldmark]
    [markup.goldmark.parser]
      wrapStandAloneImageWithinParagraph = false
      [markup.goldmark.parser.attribute]
        block = true
```

This makes it possible to add Markdown attributes (e.g. CSS classes) on standalone images:

```
![Gravel Calls](gravel-calls.jpeg)
{width="200" alt="Gravel Calls" class="center"}
```

![Gravel Calls](./gravel-calls.jpeg)
{width="200" alt="Gravel Calls" class="center"}

Note that the attributes must go on the line following the image tag. Putting them on the same line won't work

## Examples

```
{{</* figure src="/img/gravel-calls.jpeg" width="200" alt="Gravel Calls" class="left" */>}}
```

{{< figure src="/img/gravel-calls.jpeg" width="200" alt="Gravel Calls" class="left" >}}

At this point we have to enter text to flow to the right of the figure

* Note that the list formatted is a bit messed up. There is no tab.
* another point
* and a third
* this is getting boring!
* and another
* almost there
* still not quite
* one more line!
* and we should be done!

```
<img src="../images/gravel-calls.jpeg" width="200" alt="Gravel Calls" class="right" >
```

<img src="../images/gravel-calls.jpeg" width="200" alt="Gravel Calls" class="right" >

At this point we have to enter text to flow to the left of the figure

* Note that the list formatting is a bit messed up. There is no tab.
* another point
* and a third
* this is getting boring!
* and another
* almost there
* still not quite
* one more line!
* and we should be done!

```
{{</* figure src="../images/gravel-calls.jpeg" width="200" alt="Gravel Calls" class="center" */>}}
```

{{< figure src="../images/gravel-calls.jpeg" width="200" alt="Gravel Calls" class="center" >}}

Note here that the image is centered with `class="center"`, and the text does not flow around.

```
<img src="../images/gravel-calls.jpeg" width="200" alt="Gravel Calls">
```

<img src="../images/gravel-calls.jpeg" width="200" alt="Gravel Calls">

Finally, if we don't use any class element, the default is for the image to be left-justified, with no text flow around.

## Notes

* [Image processor](https://gohugo.io/content-management/image-processing/) -  Hugo has a built in image processor for pre-processing images. It's use optional. A list of the filtering functions can be found at [Image Filters](https://gohugo.io/functions/images/)
* [Markdown Processing Update in Release v0.108.8](https://github.com/gohugoio/hugo/releases/tag/v0.108.0) - With Hugo `v0.108.0` you can render standalone Markdown images without a surrounding paragraph. Both the HTML- and CommonMark-specification defines image as an inline element. For Markdown, this has meant that if you put an image on its own (not _inlined_ in another paragraph), it would be wrapped in `<p></p>` tags, even if you provide your own [Render Hook Template](https://gohugo.io/templates/render-hooks/).
