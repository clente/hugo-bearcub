# ᕦʕ •ᴥ•ʔᕤ Bear Cub

[![github pages](https://github.com/clente/hugo-bearcub/actions/workflows/gh-pages.yml/badge.svg)](https://github.com/clente/hugo-bearcub/actions/workflows/gh-pages.yml)
[![MIT license](https://img.shields.io/github/license/clente/hugo-bearcub)](https://github.com/clente/hugo-bearcub/blob/main/LICENSE)

## Overview

🐻 A lightweight [Hugo](https://gohugo.io/) theme based on [Bear
Blog](https://bearblog.dev) and [Hugo Bear
Blog](https://github.com/janraasch/hugo-bearblog).

**Bear Cub** takes care of speed and optimization, so you can focus on writing
good content. It is free, multilingual, optimized for search engines,
no-nonsense, responsive, light, and fast. Really fast.

## Installation

Follow Hugo's [quick start](https://gohugo.io/getting-started/quick-start/) to
create an empty website and then clone **Bear Cub** into the themes directory as
a [Git submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules):

```sh
git submodule add https://github.com/clente/hugo-bearcub themes/hugo-bearcub
```

To finish off, append a line to the site configuration file:

```sh
echo 'theme = "hugo-bearcub"' >> hugo.toml
```

## Features

Like [Bear Blog](https://bearblog.dev), this theme:
- Is free and open source
- Looks great on any device
- Makes tiny (~5kb), optimized, and awesome pages
- Has no trackers, ads, or scripts
- Automatically generates an RSS feed

But that's not all! **Bear Cub** is also...

### Accessible

**Bear Cub** has a few accessibility upgrades when compared to its predecessors.
The color palette has been overhauled to make sure everything is
[readable](https://web.dev/color-and-contrast-accessibility/) for users with low
vision impairments or color deficiencies, and some interactive elements were
made bigger to facilitate [clicking](https://web.dev/accessible-tap-targets/)
for users with a motor impairment.

These small changes mean that **Bear Cub** passes Google's [PageSpeed
test](https://pagespeed.web.dev/report?url=https%3A%2F%2Fclente.github.io%2Fhugo-bearcub%2F)
with flying colors.

![PageSpeed score](https://raw.githubusercontent.com/clente/hugo-bearcub/main/images/pagespeed.webp)

### Secure

[**Bear Cub**'s demo](https://clente.github.io/hugo-bearcub/) is hosted on GitHub
and therefore I'm not in control of its [Content Security
Policy](https://infosec.mozilla.org/guidelines/web_security#content-security-policy).
However, the theme itself was made with security in mind: there are no inline
styles and it uses no JavaScript at all.

If you want to improve your [Mozilla
Observatory](https://observatory.mozilla.org/) score even further, you should be
able to simply add a few headers to your hosting service's configuration (e.g.
[Netlify](https://docs.netlify.com/routing/headers/) or [Cloudflare
Pages](https://developers.cloudflare.com/pages/platform/headers/)) and never
have to think about it again. My `_headers` file, for example, looks like this:

```
/*
  X-Content-Type-Options: nosniff
  Strict-Transport-Security: "max-age=31536000; includeSubDomains; preload" env=HTTPS
  Cache-Control: max-age=31536000, public
  X-Frame-Options: deny
  Referrer-Policy: no-referrer
  Feature-Policy: microphone 'none'; payment 'none'; geolocation 'none'; midi 'none'; sync-xhr 'none'; camera 'none'; magnetometer 'none'; gyroscope 'none'
  Content-Security-Policy: default-src 'none'; manifest-src 'self'; font-src 'self'; img-src 'self'; style-src 'self'; form-action 'none'; frame-ancestors 'none'; base-uri 'none'
  X-XSS-Protection: 1; mode=block
```

### Multilingual

If you need to write a blog that supports more than one language, **Bear Cub**
has you covered! Check out the demo's [`hugo.toml`
file](https://github.com/clente/hugo-bearcub/blob/main/exampleSite/hugo.toml)
for a sample of how you can setup multilingual support.

By default, the theme creates a translation button that gets disabled when the
current page is only available in any other language. You can also choose to
hide this button (instead of disabling it) by setting `hideUntranslated =
false`.

### More

Every once in a while, as I keep using **Bear Cub**, I notice that there is some
functionality missing. Currently, these are the "advanced features" that I have
already implemented:

- Full-text RSS feed: an enhanced RSS feed template that includes the (properly
  encoded) full content of your posts in the feed itself.
- Static content: you can create empty blog entries that act as links to static
  files by including `link: "{url}"` in a post's [front
  matter](https://gohugo.io/content-management/front-matter/). You can also add
  `render: false` to your [build
  options](https://gohugo.io/content-management/build-options/#readout) to avoid
  rendering blank posts.
- Skip link: a "skip to main content" link that is temporarily invisible, but
  can be focused by people who need a keyboard to navigate the web (see [PR
  #5](https://github.com/clente/hugo-bearcub/pull/5) by
  [@2kool4idkwhat](https://github.com/2kool4idkwhat) for more information).
- Reply by email: if you supply an email address, the theme creates a "Reply to
  this post by email" button at the end of every post (see Kev Quirk's [original
  implementation](https://kevquirk.com/adding-the-post-title-to-my-reply-by-email-button)).
- `absfigure` shortcode: a shortcut to use the `figure` shortcode that also
  converts relative URLs into absolute URLs by using the `absURL` function.
- Single-use CSS (EXPERIMENTAL): you can add some styles to a single page by
  writing the CSS you need in `assets/{custom_css}.css` and then including
  `style: "{custom_css}.css"` in the [front
  matter](https://gohugo.io/content-management/front-matter/) of said page.
- Conditional CSS (EXPERIMENTAL): since **Bear Cub** does syntax highlighting
  without inline styles (see `hugo.toml` for more information), it only load its
  `syntax.css` if, and only if, a code block is actually present in the current
  page.
- Alternative "Herman" style (EXPERIMENTAL): if you want to check out a more
  modern CSS style, you can change the `themeStyle` parameter to `"herman"` in
  order to activate [Herman Martinus's](https://herman.bearblog.dev/) version of
  the [Blogster Minimal](https://blogster-minimal.netlify.app/) theme for
  [Astro](https://astro.build/).
- Dynamic social card generation (EXPERIMENTAL): if you don't add preview images
  to a post, this template will generate one based on the title. You can see an
  example below.

![Social card example](https://raw.githubusercontent.com/clente/hugo-bearcub/main/images/social_card.webp)

## Configuration

**Bear Cub** can be customized with a `hugo.toml` file. Check out the
[configuration](https://github.com/clente/hugo-bearcub/blob/main/exampleSite/hugo.toml)
of the [demo](https://clente.github.io/hugo-bearcub/) for more information.

```toml
# Basic config
baseURL = "https://example.com"
theme = "hugo-bearcub"
copyright = "John Doe (CC BY 4.0)"
defaultContentLanguage = "en"

# Generate a nice robots.txt for SEO
enableRobotsTXT = true

# Setup syntax highlighting without inline styles. For more information about
# why you'd want to avoid inline styles, see
# https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/style-src#unsafe_inline_styles
[markup]
  [markup.highlight]
    lineNos = true
    lineNumbersInTable = false
    # This allows Bear Cub to use a variation of Dracula that is more accessible
    # to people with poor eyesight. For more information about color contrast
    # and accessibility, see https://web.dev/color-and-contrast-accessibility/
    noClasses = false

# Multilingual mode config. More for information about how to setup translation,
# see https://gohugo.io/content-management/multilingual/
[languages]
  [languages.en]
    title = "Bear Cub"
    languageName = "en-US 🇺🇸"
    LanguageCode = "en-US"
    contentDir = "content"
    [languages.en.params]
      madeWith = "Made with [Bear Cub](https://github.com/clente/hugo-bearcub)"
  [languages.pt]
    title = "Bear Cub"
    languageName = "pt-BR 🇧🇷"
    LanguageCode = "pt-BR"
    contentDir = "content.pt"
    [languages.pt.params]
      madeWith = "Feito com [Bear Cub](https://github.com/clente/hugo-bearcub)"

[params]
  # The description of your website
  description = "Bear Cub Demo"

  # The path to your favicon
  favicon = "images/favicon.png"

  # These images will show up when services want to generate a preview of a link
  # to your site. Ignored if `generateSocialCard = true`. For more information
  # about previews, see https://gohugo.io/templates/internal#twitter-cards and
  # https://gohugo.io/templates/internal#open-graph
  images = ["images/share.webp"]

  # This title is used as the site_name on the Hugo's internal opengraph
  # structured data template
  title = "Bear Cub"

  # Dates are displayed following the format below. For more information about
  # formatting, see https://gohugo.io/functions/format/
  dateFormat = "2006-01-02"

  # If your blog is multilingual but you haven't translated a page, this theme
  # will create a disabled link. By setting `hideUntranslated` to true, you can
  # have the theme simply not show any link
  hideUntranslated = false

  # (EXPERIMENTAL) This theme has two options for its CSS styles: "original" and
  # "herman". The former is what you see on Bear Cub's demo (an optimized
  # version of Hugo Bear Blog), while the latter has a more modern look based on
  # Herman Martinus's version of the Blogster Minimal theme for Astro.
  themeStyle = "original"

  # (EXPERIMENTAL) This theme is capable of dynamically generating social cards
  # for posts that don't have `images` defined in their front matter; By setting
  # `generateSocialCard` to false, you can prevent this behavior. For more
  # information see layouts/partials/social_card.html
  generateSocialCard = true

  # Social media. Delete any item you aren't using to make sure it won't show up
  # in your website's metadata.
  [params.social]
    twitter = "example" # Twitter handle (without '@')
    facebook_admin = "0000000000" # Facebook Page Admin ID

  # Author metadata. This is mostly used for the RSS feed of your site, but the
  # email is also added to the footer of each post
  [params.author]
    name = "John Doe" # Your name as shown in the RSS feed metadata
    email = "me@example.com" # Added to the footer so readers can reply to posts
```

## Contributing

If you come across any problems while using **Bear Cub**, you can file an
[issue](https://github.com/clente/hugo-bearcub/issues) or create a [pull
request](https://github.com/clente/hugo-bearcub/pulls).
