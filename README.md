# ProtProtocols main page

This is the source of the ProtProtocols GitHub page. The rendered page can be found at https://protprotocols.github.io

This README is intended as an (internal) documentation of how to work with this page.

## Setup

The page is using [Jekyl](https://jekyllrb.com/) to build the page. This is done automatically through GitHub page's Jekyl rendering system. This system automatically rebuilds the page whenever changes are committed to the master branch (with a limit of 10 changes / day).

For this page, we use the [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) template. The template contains several additional features to build TOC / sidebars etc. Therefore, please refer to the [template's documentation](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/) before adapting the site layout.

### Local installation

It is **highly** recommended to test the page locally before deploying changes to the master branch. Jekyl requires Ruby. After installing Ruby, the easiest method to install Jekyl is through bundler:

```bash
gem install bundler jekyll

# move into this directory
cd /this/directory

# install all required tools to create the site
bundler update
```

This setup allows you to launch a web server that automatically updates the rendered page whenever you change the source code:

```bash
bundle exec jekl serve
```

### Using a local version of the theme

Since we need to reference the [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) template as a `remote_theme` this system also always downloads an updated version of the theme. To prevent this, adapt the `_config.yml` file:

```
# disable the remote theme
#remote_theme: mmistakes/minimal-mistakes
# and use the local version
theme: minimal-mistakes-jekyll
```

**IMPORTANT:** This needs to be reverted before uploading the changes!

## Site structure

All pages are markdown formatted files with a specific YAML formatted [front matter](https://jekyllrb.com/docs/front-matter/). This means, that every file has to start with this header:

```
---
layout: post
title: Blogging Like a Hacker
---
```

The [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) template uses this front matter quite extensively to format, for example, the landing page.

All pages can be found in the `_pages` directory. The `permalink:` attribute defines the URL location that the file represents. 

All static files (ie. images) are in the `assets` directory.

We currently do not use Jekyl's posting system. Nevertheless, I did not remove the `_posts` directory for now.

The `_data` directory contains any structured (YAML, tsv, etc.) datafiles. At the time of writing, this only includes the `navigation.yml` file describing the navigation structure.
