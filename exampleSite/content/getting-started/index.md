+++
date = "2016-03-09T00:11:02+01:00"
title = "Getting started"
+++

## Installation

### Installing Hugo

Hugo itself is just a single binary without dependencies on expensive runtimes like Ruby, Python or PHP and without dependencies on any databases. You just need to download the [latest version](https://github.com/spf13/hugo/releases). For more information read the official [installation guides](http://gohugo.io/overview/installing/).

Let's make sure Hugo is set up as expected. You should see a similar version number in your terminal:

```sh
hugo version
# Hugo Static Site Generator v0.15 BuildDate: 2016-01-03T12:47:47+01:00
```

### Installing Material

Next, assuming you have Hugo up and running the `hugo-material-docs` theme can be installed with `git`:

```sh
# create a new Hugo website
hugo new site my-awesome-docs

# move into the root folder of your website
cd my-awesome-docs

# download the theme
git clone git@github.com:digitalcraftsman/hugo-material-docs.git themes
```

## Setup

Next, take a look in the `exampleSite` folder at `themes/hugo-material-docs/`. This directory contains an example config file and the content that you are currently reading. It serves as an example setup for your documentation. 

Copy at least the `config.toml` in the root directory of your website. Overwrite the existing config file if necessary. 

Hugo includes a development server, so you can view your changes as you go -
very handy. Spin it up with the following command:

``` sh
hugo server
```

Now you can go to [localhost:1313](http://localhost:1313) and the Material
theme should be visible. You can now start writing your documentation, or read
on and customize the theme through some options.

## Configuration

Before you are able to deploy your documentation you should take a few minute to adjust some information in the `config.toml`. Open the file in an editor:

```toml
baseurl = "http://replace-this-with-your-hugo-site.com/"
languageCode = "en-us"
title = "Material Docs"

[params]
  # General information
  author = "Digitalcraftsman"
  description = "A material design theme for documentations."
  copyright = "Released under the MIT license"
```

## Options

### Github integration

If your project is hosted on GitHub, add the repository link to the
configuration. If the `provider` equals **GitHub**, the Material theme will
add a download and star button, and display the number of stars:

```toml
[params]
  # Repository
  provider = "GitHub"
  repo_url = "https://github.com/digitalcraftsman/hugo-material-docs"
```

### Adding a version

In order to add the current version next to the project banner inside the
drawer, you can set the variable `version`:

```toml
[params]
  version = "1.0.0"
```

This will also change the link behind the download button to point to the
archive with the respective version on GitHub, assuming a release tagged with
this exact version identifier.

### Adding a logo

If your project has a logo, you can add it to the drawer/navigation by defining
the variable `logo`. Ideally, the image of your logo should have
rectangular shape with a minimum resolution of 128x128 and leave some room
towards the edges. The logo will also be used as a web application icon on iOS.
Save your logo somewhere in the `static/` folder and reference the file relative to this location:

```toml
[params]
  logo = "images/logo.png"
```


### Google Analytics

You can enable Google Analytics by replacing `UA-XXXXXXXX-X` with your own tracking code.

```toml
[params]
  # Google Analytics
  google_analytics = ["UA-XXXXXXXX-X", "auto"]
```

### Small tweaks

This theme provides a simple way for making small adjustments, that is changing
some margins, centering text, etc. Simply put the CSS and Javascript files that
contain your adjustments in the `static/` directory (ideally in subdirectories of their own) and include them via the `custom_css` and `custom_js`
variables in your `config.toml`. Reference the files with relative to `static/`:

```toml
[params]
  # Custom assets
  custom_css = [
    "foo.css",
    "bar.css"
  ]

  custom_js  = ["buzz.js"]
```

### Changing the color palette

Material defines a default hue for every primary and accent color on Google's
material design [color palette][]. This makes it very easy to change the overall look of the theme. Just set the variables `palette.primary` and `palette.accent` to one of the colors defined in the palette:

```toml
[params.palette]
  primary = "red"
  accent  = "light green"
```

Color names can be written upper- or lowercase but must match the names of the
material design [color palette](http://www.materialui.co/colors). Valid values are: _red_, _pink_, _purple_, _deep purple_, _indigo_, _blue_, _light blue_, _cyan_, _teal_, _green_, _light
green_, _lime_, _yellow_, _amber_, _orange_, _deep orange_, _brown_, _grey_ and
_blue grey_. The last three colors can only be used as a primary color.

![Color palette](/images/colors.png)

If the color is set via this configuration, an additional CSS file called
`palettes.css` is included that defines the color palettes.

### Changing the font family

Material uses the [Ubuntu font family](http://font.ubuntu.com) by default, specifically the regular sans-serif type for text and the monospaced type for code. Both fonts are loaded from [Google Fonts](https://www.google.com/fonts) and can be easily changed to other fonts, like for example Google's own [Roboto font](https://www.google.com/fonts/specimen/Roboto):

```toml
[params.font]
      text = "Roboto"
      code = "Roboto Mono"
```

The text font will be loaded in font-weights 400 and **700**, the monospaced
font in regular weight.

### Adding a GitHub and Twitter account

If you have a GitHub and/or Twitter account, you can add links to your
accounts to the drawer by setting the variables `author.github` and
`author.twitter` respectively:

``` toml
[social]
  twitter = ""
  github  = "digitalcraftsman"
```

### Adding menu entries

Once you created your first content files you can link them manually in the sidebar on the left. A menu entry has the following schema:

```toml
[[menu.main]]
  name   = "Material"
  url    = "/"
  weight = 0
```

`name` is the title displayed in the menu and `url` the relative URL to the content. The `weight` attribute allows you to modify the order of the menu entries. A menu entry appears further down the more weight you add.

### Markdown extensions

Hugo uses [Blackfriday](https://github.com/russross/blackfriday) to process your content. For a detailed description of all options take a look at the [Blackfriday configuration](http://gohugo.io/overview/configuration/#configure-blackfriday-rendering) section in the Hugo documentation.

```toml
[blackfriday]
  pygmentsuseclasses = true
  smartypants = true
  fractions = true
  smartDashes = true
  plainIDAnchors = true
```