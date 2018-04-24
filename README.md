# hexo-theme-bootstrap4-reveal

A simple [Bootstrap] v4 blog theme for [Hexo].

Based on the [Hexo Bootstrap theme](https://github.com/cgmartin/hexo-theme-bootstrap-blog).

[Demo site](http://raybo.org/fid)

## Setup Instructions

### Install

**This theme requires Hexo 2.4 and above.**

1) Install theme:

```bash
$ git clone https://github.com/planetoftheweb/hexo-theme-bootstrap4-reveal
```

2) (optional) Install [hexo-processor-static](https://github.com/planetoftheweb/hexo-processor-static) to make copying of markdown slides work.

```bash
$ npm install hexo-processor-static --save
```

### Enable

Modify the `theme` setting in `_config.yml` to `bootstrap-blog`.

### Update

```bash
cd themes/bootstrap-blog
git pull
```

## Configuration

```yml
# File: themes/bootstrap-blog/_config.yml

# Header
navbar_brand: false
menu:
  Home: index.html
  Archives: archives/
rss: /atom.xml

# Content
excerpt_link: Read More
fancybox: true

# Sidebar
widgets:
- about         # See also: `about_content`
- category
- tag
- tagcloud
- archives
- recent_posts
about_widget_content: >
  <p>Etiam porta <em>sem malesuada magna</em> mollis euismod.
  Cras mattis consectetur purus sit amet fermentum. Aenean
  lacinia bibendum nulla sed consectetur.</p>

# Miscellaneous
google_analytics:
favicon:
twitter:
google_plus:
```

- **navbar_brand** - The HTML content for an optional ["navbar-brand"](http://getbootstrap.com/components/#navbar-brand-image). Can be text or an image. `false` to hide.
- **menu** - Navigation menu (map of Titles to URLs)
- **rss** - RSS link (ie. "/atom.xml")
- **excerpt_link** - "Read More" link at the bottom of excerpted articles. `false` to hide the link.
- **fancybox** - Enable [Fancybox] for images
- **widgets** - Enable sidebar widgets ([more info below](#sidebar))
- **about_widget_content** - The HTML content for the "About" sidebar widget ([more info below](#sidebar))
- **google_analytics** - Google Analytics ID
- **favicon** - Favicon path (ie. '/favicon.ico')
- **twitter_id** - Twitter ID of the author (ie. `@c_g_martin`)
- **google_plus** - Google+ profile link

Instead of editing the layout's configuration file directly, you can override the theme settings from your project's root `_config.yml`, ie.:
```yml
theme_config:
  # Header
  navbar_brand: <img src="/navbrand.png">
  menu:
    Home: index.html
    Archives: archives/
    'Another Page': page/index.html
  widgets:
   - about
   - category
   - archive
   - recent_posts
   - tag
  about_widget_content: >
    <p>This is <strong>custom content</strong> for the
    "about" sidebar widget.</p>
```

## Features

### Front-Matter Extras

Optional settings in the front-matter can be added for various effects:
```yml
---
author: Author Name   # displays the post's author
photos:               # displays a Bootstrap thumbnail gallery
- images/HNCK0537.jpg
- images/HNCK6173.jpg
---
```

### Fancybox

This theme uses [Fancybox] to showcase your photos. You can use the image Markdown syntax or fancybox tag plugin to add your photos.

Usage:
```
![img caption](img url)

~or~

{% fancybox img_url [img_thumbnail] [img_caption] %}
```

### Sidebar

This theme provides 6 built-in widgets that can be displayed in the sidebar:

- [about](./layout/_widget/about.ejs) \*
- [category](./layout/_widget/category.ejs)
- [tag](./layout/_widget/tag.ejs)
- [tagcloud](./layout/_widget/tagcloud.ejs)
- [archives](./layout/_widget/archives.ejs)
- [recent_posts](./layout/_widget/recent_posts.ejs)

All widgets are enabled by default. You can toggle them on/off with the `widgets` setting in the theme's [_config.yml](./config.yml).

\* **NOTE**: The "about" widget contains static Lorem Ipsum text by default. You'll want to edit the `about_widget_content` setting for your site or disable the widget in the [theme config](./config.yml). You can also modify the widget file itself to include contents from a Markdown page:
```html
<!-- file: ./layout/_widget/about.ejs -->
<div class="sidebar-module sidebar-module-inset">
  <h4>About</h4>
  <%- site.pages['data'].find(function(p) { return p.path === 'about/index.html'; }).content %>
</div>
```
...then run `hexo new page about` to create the Markdown page.

### Bootstrap Paginator Helper

A custom `bs_paginator()` helper is used to produce [Bootstrap-compatible pagination markup](http://getbootstrap.com/components/#pagination). It is a drop-in replacement for Hexo's built-in `paginator()`.

```
<%- bs_paginator({
      prev_text: '<i class="fa fa-chevron-left"></i> Prev',
      next_text: 'Next <i class="fa fa-chevron-right"></i>'
    }) %>
```

## License

[MIT](LICENSE)

[Hexo]: http://zespia.tw/hexo/
[Fancybox]: http://fancyapps.com/fancybox/
[Bootstrap]: http://getbootstrap.com/