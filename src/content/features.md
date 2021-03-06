---
type: mpage
title: "Features of Strawberry"
---

Strawberry is built upon the strong foundation of [Hugo](https://gohugo.io).
99% of our features (and code for that matter) come from Hugo.
You can learn about all of Hugo's features (if you're unfamiliar) [here](https://gohugo.io/about/features/).


## Features Unique to Strawberry

### Sitemap Page Exclusion

You can exclude pages from the built-in Sitemap by excluding it in a page's Front Matter.
It would look something like this:

```
---
title: "My Page"
description: "This is a page that is public but I don't want it in my sitemap.
date: "2020-06-13"
sitemap:
  exclude: true
---

My page.... blah blah blah.
```

While this setting can be done page-by-page to opt them out of the sitemap, you can also set this in your Strawberry config file to opt-out all pages by default.
Then, you can manually opt-in pages.

### Menu Items Support Opening in New Tabs

If you have a menu item that you'd prefer to open in a new tab (or window, depending on browser), you can now do so via the Strawberry config file.
Here's an example:

```yaml
#... gotham config

menu:
  main:
    - name: "Home"
      url: "/"
    - name: "Blog"
      url: "/blog/"
    - name: "Twitter"
      url: "https://twitter.com/StrawberrySSG"
      newtab: true
```

In the example above, the homepage and the blog will open in the same tab when clicked, as expected.
The Twitter menu item will open in a new tab.
This is a common practice when linking to external URLs.

### Open Development Site in Browser

When running the development server locally (gotham server), you can now optionally open the dev URL in your default browser.
This can be done using the `--open` flag. For example:

```bash
gotham serve --open
```

### YouTube Shortcode

The YouTube shortcode that already comes with Strawberry (and Hugo) got three additional parameters:

- The shortcode has a title parameter.
- The shortcode has start and stop parameters, measured in seconds.

Here's example usage:

```
{{</* youtube id="tz-NErQZu6k" title="FelicianoTech's first YouTube video" start="11" */>}}
```

which would render as:

{{< youtube id="tz-NErQZu6k" title="FelicianoTech's first YouTube video" start="11" >}}

### QR Code Shortcode

There's a new shortcode available called "qrcode".
You can pass it a URL and it will output that URL encoded as a QR code to the page.
This shortcode shares the HTML and features of the `figure` shortcode minus the embedded link.
This means parameters such as `alt` and `class` can be used.
Instead of `width` and `height`, this shortcode has a `size` parameter to specify the dimensions of the square.
Usage:

```
{{</* qrcode url="https://google.com" */>}}
```

which would render as:

{{< qrcode url="https://google.com" >}}

### Digital Asset Links

A Strawberry site can generate an Asset Links file (`assetlinks.json`) by providing two key bits of information in your Strawberry config.

```yaml
#... gotham config
assetLinksPackageName: "<my-package-name>"
assetLinksFingerprint: "<my-android-certificate-sha>"
```

Resources:

- https://developer.android.com/training/app-links/verify-site-associations
- https://developers.google.com/digital-asset-links/tools/generator
- https://developers.google.com/digital-asset-links/v1/getting-started

### Mastodon Shortcode

Embed Mastodon toots in your Strawberry pages with this Mastodon shortcode.
You can pass the toot URL and optionally, a width and height.
Keep in mind that the width and height are considered suggestions to Mastodon and it will render mostly based on the content it's trying to show.

Usage:

```
{{</* mastodon url="https://mastodon.social/@Gargron/105303408810292711" */>}}
```

which would render as:

{{< mastodon url="https://mastodon.social/@Gargron/105303408810292711" >}}


## Changes from Hugo

**Goldmark** -  the Markdown renderer has a setting on whether or not to allow HTML in your Markdown files.
Hugo has this set to false/off by default while Strawberry has this set to true/on.
