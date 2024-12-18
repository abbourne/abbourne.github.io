---
title: "Colophon - How this Site is Made"
description: "An overview of Bill Bourne's site discussing cycling, technology and other topics"
keywords:
  - "Hugo"
  - "Markdown"
weight: 3
type: doc
---

{{< figure src="../images/hugo-logo-200px.png" width="150" alt="Hugo logo" class="right" >}}
This site is written in [Markdown](https://www.markdownguide.org/) and generated with the static site generator (SSG) [Hugo](https://gohugo.io/). Markdown is a simple plain text document format that can be easily and quickly processed to generate html, pdf, .docx, and a number of other file formats. I use it for just about all my writing - for documents and articles (I avoid Microsoft Word at all costs!), note taking, and for writing web pages. Hugo quickly generates an efficient website. Since the website is made up only of static webpages and a little JavaScript, it renders fast.

I started with the [Mainroad](https://github.com/Vimux/Mainroad) theme, and gradually added customizations and extensions. (I spend way too much time fretting about formatting and not nearly enough time actually writing content - And the results are pretty mediocre in any case!)

Hugo can run a local webserver for development. Hugo watches for file changes - when I'm writing on my laptop and I save a file, Hugo regenerates the site in less than a second, and I can see my results instantly.

An advantage of static sites, or to be precise, sites that use the [Jamstack](https://jamstack.org/) architecture is that there are numerous options for great free, reliable hosting on cloud infrastructure with quite rich features. I'm experimenting with [GitHub Pages](https://pages.github.com/) and [Netlify](https://www.netlify.com/). Both support Hugo, as well as several other SSGs.

The source for the site is stored in [GitHub](https://github.com/abbourne/abbourne.github.io). A push to the Master branch triggers a production build and deploy. It takes about 30 seconds from entering `git push` on my laptop until the site is live on the web.
