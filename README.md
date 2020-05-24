# jemsugo

> Jemsu Hugo extensions: Just some shortcodes and stuff

This is just an experiment to see if I can externalize my (equally experimental) [hugo] [shortcodes].  

The idea would be to leverage [theme components] so that I could re-use these shortcodes across different projects just my cloning (or better: `git submodule`'ing) this repository into a sites `/themes/` directory and then change `config.toml` from

```toml
theme = "hugo-coder"
```

to

```toml
theme = ["jemsugo", "hugo-coder"]
```

This *should* (if I understood the docs correctly) make it possible to use these shortcodes without having to copy paste them into a sites `/layouts/shortcodes` _and_ without having to add them to a specific theme.


[hugo]: https://gohugo.io/
[shortcodes]: https://gohugo.io/templates/shortcode-templates
[theme components]: https://gohugo.io/hugo-modules/theme-components