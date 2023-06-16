---
title: "Using PaperMod's rawhtml shortcode to embed HTML code"
date: 2023-06-16T06:43:41Z
author: "marcusz"
draft: true
tags: ["demos", "useful", "embeds", "hugo", "papermod", "web", "tech", "tricks"]
description: "rawhtml to the rescue!"
---
Normally when embedding something with hugo page, you would need to learn short codes which may not be easy to just copy the HTML snippet into the markdown document.

However using PaperMod theme makes it easier to insert raw html/css/javascript code on the markdown directly. Simply put a shorcode and a HTML snippet onto that short code in your markdown document.
```html
{{</* rawhtml */>}}
<h2>This is a heading</h2>
<p>This is a paragraph</p>
{{</*/ rawhtml  */>}}
```

Here is the example of rawhtml embedding an image file and a YouTube video
{{< rawhtml >}}
<h3>OneDrive Attachment</h3>
<img src="https://blz04pap006files.storage.live.com/y4mqvM95WpRnB7q_mtw9kwdVqe425gq9Xd7ZL_YeNBKu5XOunXzM5VDt2_wdI9g_OVhVd-TUHgQZUvgOrhGhwk3pQPglb8dOD6XphgLonTR8kYahw3wWRHke7LNWelMY48UJbZvbPnx5Jif64jFxQ0AgUOWq4Pvvm76erwugyX3BnJRmSjFEiIYjhSXm_YV83Av?width=827&height=821&cropmode=none" width="256" height="254" />

<h3>YouTube video embed</h3>
<iframe width="320" height="240" src="https://www.youtube.com/embed/dQw4w9WgXcQ" title="Rick Astley - Never Gonna Give You Up (Official Music Video)" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
{{</ rawhtml >}}
