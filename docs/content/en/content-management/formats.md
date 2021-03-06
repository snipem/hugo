---
title: Content Formats
linktitle: Content Formats
description: Both HTML and Markdown are supported content formats.
date: 2017-01-10
publishdate: 2017-01-10
lastmod: 2017-04-06
categories: [content management]
keywords: [markdown,asciidoc,mmark,pandoc,content format]
menu:
  docs:
    parent: "content-management"
    weight: 20
weight: 20	#rem
draft: false
aliases: [/content/markdown-extras/,/content/supported-formats/,/doc/supported-formats/]
toc: true
---

You can put any file type into your `/content` directories, but Hugo uses the `markup` front matter value if set or the file extension (see `Markup identifiers` in the table below) to determine if the markup needs to be processed, e.g.:

* Markdown converted to HTML
* [Shortcodes](/content-management/shortcodes/) processed
* Layout applied

## List of content formats

The current list of content formats in Hugo:

| Name  | Markup identifiers | Comment | 
| ------------- | ------------- |-------------|
| Goldmark  | md, markdown, goldmark  |Note that you can set the default handler of `md` and `markdown` to something else, see [Configure Markup](/getting-started/configuration-markup/).{{< new-in "0.60.0" >}} |
| Blackfriday | blackfriday  |Blackfriday will eventually be deprecated.|
|MMark|mmark|Mmark is deprecated and will be removed in a future release.|
|Emacs Org-Mode|org|See [go-org](https://github.com/niklasfasching/go-org).|
|AsciiDoc|asciidoc, adoc, ad|Needs AsciiDoc or [Asciidoctor][ascii] installed.|
|RST|rst|Needs [RST](http://docutils.sourceforge.net/rst.html) installed.|
|Pandoc|pandoc, pdc|Needs [Pandoc](https://www.pandoc.org/) installed.|
|HTML|html, htm|To be treated as a content file, with layout, shortcodes etc., it must have front matter. If not, it will be copied as-is.|

The `markup identifier` is fetched from either the `markup` variable in front matter or from the file extension. For markup-related configuration, see [Configure Markup](/getting-started/configuration-markup/).


## External Helpers

Some of the formats in the table above needs external helpers installed on your PC. For example, for AsciiDoc files, 
Hugo will try to call the `asciidoctor` or `asciidoc` command. This means that you will have to install the associated 
tool on your machine to be able to use these formats.

Hugo passes reasonable default arguments to these external helpers by default:

- `asciidoc`: `--no-header-footer --safe -`
- `asciidoctor`: `--no-header-footer --safe --trace -`
- `rst2html`: `--leave-comments --initial-header-level=2`
- `pandoc`: `--mathjax`

{{% warning "Performance of External Helpers" %}}
Because additional formats are external commands generation performance will rely heavily on the performance of the external tool you are using. As this feature is still in its infancy, feedback is welcome.
{{% /warning %}}

### External Helper AsciiDoc

[AsciiDoc](https://github.com/asciidoc/asciidoc) implementation EOLs in Jan 2020. 
AsciiDoc development is being continued under [Asciidoctor](https://github.com/asciidoctor). The format AsciiDoc 
remains of course. Please continue with the implementation Asciidoctor.

### External Helper Asciidoctor

The Asciidoctor community offers a wide set of tools for the AsciiDoc format that can be installed additionally to Hugo. 
[See the Asciidoctor docs for installation instructions](https://asciidoctor.org/docs/install-toolchain/).

Referencing chapters e.g. by [include](https://asciidoctor.org/docs/asciidoc-syntax-quick-reference/#include-files) 
keyword or rendering [asciidoctor-diagram](https://asciidoctor.org/docs/asciidoctor-diagram/) requires Hugo to set the
helper args `--base-dir` and `outdir=`. These will be added if enabled by setting `workingFolderCurrent = true`. All Asciidoctor 
args can be customized in Hugo. E.g.

```
[markup.asciidocext]
    args = ["--no-header-footer", "-r", "asciidoctor-html5s", "-b", "html5s", "-r", "asciidoctor-diagram"]
    workingFolderCurrent = true
```

External asciidoctor requires Hugo rendering to disk to a specific destination folder. It is required to run Hugo with the command option `--destination`!

In a complex Asciidoctor environment it is sometimes helpful to debug the exact call to your external helper with all 
parameters. Run Hugo with `-v`. You will get an output like

```
INFO 2019/12/22 09:08:48 Rendering book-as-pdf.adoc with C:\Ruby26-x64\bin\asciidoctor.bat using asciidoc args [--no-header-footer -r asciidoctor-html5s -b html5s -r asciidoctor-diagram --base-dir D:\prototypes\hugo_asciidoc_ddd\docs -a outdir=D:\prototypes\hugo_asciidoc_ddd\build -] ...
```

## Learn Markdown

Markdown syntax is simple enough to learn in a single sitting. The following are excellent resources to get you up and running:

* [Daring Fireball: Markdown, John Gruber (Creator of Markdown)][fireball]
* [Markdown Cheatsheet, Adam Pritchard][mdcheatsheet]
* [Markdown Tutorial (Interactive), Garen Torikian][mdtutorial]
* [The Markdown Guide, Matt Cone][mdguide]

[`emojify` function]: /functions/emojify/
[ascii]: https://asciidoctor.org/
[bfconfig]: /getting-started/configuration/#configuring-blackfriday-rendering
[blackfriday]: https://github.com/russross/blackfriday
[mmark]: https://github.com/miekg/mmark
[config]: /getting-started/configuration/
[developer tools]: /tools/
[emojis]: https://www.webpagefx.com/tools/emoji-cheat-sheet/
[fireball]: https://daringfireball.net/projects/markdown/
[gfmtasks]: https://guides.github.com/features/mastering-markdown/#syntax
[helperssource]: https://github.com/gohugoio/hugo/blob/77c60a3440806067109347d04eb5368b65ea0fe8/helpers/general.go#L65
[hl]: /content-management/syntax-highlighting/
[hlsc]: /content-management/shortcodes/#highlight
[hugocss]: /css/style.css
[ietf]: https://tools.ietf.org/html/
[mathjaxdocs]: https://docs.mathjax.org/en/latest/
[mdcheatsheet]: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
[mdguide]: https://www.markdownguide.org/
[mdtutorial]: https://www.markdowntutorial.com/
[Miek Gieben's website]: https://miek.nl/2016/march/05/mmark-syntax-document/
[mmark]: https://github.com/mmarkdown/mmark
[org]: https://orgmode.org/
[pandoc]: https://www.pandoc.org/
[Pygments]: http://pygments.org/
[rest]: http://docutils.sourceforge.net/rst.html
[sc]: /content-management/shortcodes/
[sct]: /templates/shortcode-templates/
