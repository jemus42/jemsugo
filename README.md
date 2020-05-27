# jemsugo

> Jemsu Hugo extensions: Just some shortcodes and stuff

This is just an experiment to see if I can externalize my (equally experimental) [hugo] [shortcodes].  

You can see them in action [on my blog's shortcode showcase I use for testing](https://blog.jemu.name/shortcodes/), but keep in mind that their appearance is largely dependant on my blog's CSS.

## Installation

The idea is to leverage hugo's [theme components] or Hugo modules to re-use these shortcodes across different projects. See [my recent blog post](https://blog.jemu.name/2020/05/hugo-theme-components-modules) for more information.

### Via `git` submodules as theme components

Install this as a submodule via `git submodule add https://github.com/jemus42/jemsugo.git themes/jemsugo` and change your `config.toml`

```toml
# From (substitute your theme name)
theme = "hugo-coder"
# To
theme = ["jemsugo", "hugo-coder"]
```

To later update (all) submodules, use `git submodule update --rebase --remote`

### Via Hugo modules (no `git` needed)

If you're going the [Hugo module route](https://blog.jemu.name/2020/05/hugo-theme-components-modules/#switching-to-hugo-modules), add to your `config.toml`

```toml
[module]
  [[module.imports]]
    path = "github.com/jemus42/jemsugo"
```

## Included shortcodes

### `addendum`

A visually distinct box for "this bit may be important" or "I figured it out after the fact" kind of content.

Usage:

```html
{{< addendum title="Note" >}}
Some content that get's *markdownified*
{{< /addendum >}}
```

### `blockquote` (not my own)

Original author: Parsia Hakimian https://github.com/parsiya/Hugo-Shortcodes  
Port of Octopress blockquote plugin http://octopress.org/docs/plugins/blockquote/ to Hugo

Included because I thought it was neat and to learn from.

### `codecaption`

I wanted to put my highlighted code inside `<figure>` tags so I could more easily use captions. The options are similiar to hugo's regular `highlight` shortcode, but with added `figure` stuff.

Based on the shortcode by Parsia Hakimian https://github.com/parsiya/Hugo-Shortcodes

Usage:

```html
{{< codecaption lang="r" caption="A code caption" >}}
library(ggplot2)

ggplot(iris, aes(x = Sepal.Width, y = Sepal.Length)) +
  geom_point(size = 2)
{{< /codecaption >}}
```

### `maintenance`

A variation of `addendum` that displays a fixed notice about how stuff is broken.  
Unlikely to be usefuly to someone else and still very much just an experiment.

Usage:

```html
{{< maintenance >}}
```


### `picturefig` (todo)

I'd like to use `<picture>` tags with varying sources inside `<figure>`, bust haven't gotten around to implementing it properly.

### `pkg` (WIP)

Write `did you know about this cool package {{< pkg "packagename" >}}` and receive a decorated version in your text.

Required `params.toml` options (or under `[Params]` in `config.toml`):

```toml
pkg_format = "{%s}" # %s is the packagename, wrap it in { } if you want
pkg_icon_cran = "<i class='fab fa-r-project'></i>" # Fontawesome icon if it has a CRAN url
pkg_icon_git = "<i class='fab fa-git-alt'></i>"    # Fontawesome icon if no CRAN url
```

The data source is a `/data/packages.yml` with entries like:

```yaml
ggplot2:
  title: Create Elegant Data Visualisations Using the Grammar of Graphics
  version: 3.3.0.9000
  maintainer: Hadley Wickham
  name: ggplot2
  url_git: https://github.com/tidyverse/ggplot2
  url_other: ''
  url_pkgdown: http://ggplot2.tidyverse.org
  url_cran: https://CRAN.R-project.org/package=ggplot2
```

…This is all still very much experimental and likely to change. I just wanted to try out data stuff /o\

### `summary`

Wrap content in `<details><summary>summary text</summary> content </details>`

Usage:

```html
{{< summary "Click to expand" >}}
Some long content
{{< /summary >}}
```

### `videofig`

A variation of the `figure` shortcode that wraps a `video` tag, but also with caption etc.

```html
{{< videofig mp4="my-file.mp4" loop=true autoplay=true caption="" >}}
```

### `wp` (not my own)

Wikipedia link genertor shortcode for Hugo  
Based on https://github.com/keltia/octopress/commit/17b975067ff86c0c7cddac4ae2c2c975b0790b6e  
Author: Parsia Hakimian https://github.com/parsiya/Hugo-Shortcodes

Also included because it looked neat and to learn from.

### `wrapfigure`

Wrap arbitrary content inside `<figure>` with, you guessed it, caption and stuff.

```html
{{< wrapfigure caption="" >}}
My figureable content
{{< /wrapfigure >}}
```

<!-- Links -->
[hugo]: https://gohugo.io/
[shortcodes]: https://gohugo.io/templates/shortcode-templates
[theme components]: https://gohugo.io/hugo-modules/theme-components
