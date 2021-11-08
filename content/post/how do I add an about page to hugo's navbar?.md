---
title: how do I add an about page to Hugo's menu bar?
date: 2021-10-24
description: Add an "about" page to Hugo's menu navigation bar without it appearing as a standalone post that appears on the home page.
keywords:
- hugo
- navigation
- navbar
- menu bar
- about
- contact
category: hugo
series:
tags: 
-
toc: false
draft: true
---
## how is it normally done?

the following method is how we would normally add an about page to hugo: 

- `/about/` section to `config.yaml`
- `about.md` page within the `content` folder (outside of the `posts` folder).

This would create a standalone "about" page that does not appear with other posts.

---

`hugo-theme-monochrome` uses hugo's built in navbar structure to determine what belongs in the navbar using each page's `yaml` settings.

there's something fiddly here. either within the yaml settings or the way html layouts currently call hugo bits.

---

## how do I add an "about" page that does not appear in the posts section using hugo-theme-monochrome?

- in the `/content/` folder, create an `/about/` folder. 
- add an `index.md` page with the following `yaml`:

```yaml
---
title: about
date: 2021-10-24
type: page
---
```

to create a menu navigation bar, add to `config.yaml`:

```yaml
menu:
  navbar: # this might be called "nav" (?) for normal hugo themes.
  - identifier: post # singular
    name: posts # plural
    title: posts
    url: /posts/ # relative to root
    weight: 1
  - identifier: category
    name: categories
    url: /categories/
    weight: 10
  - identifier: about
    name: about
    url: /about/
    weight: 11

```

the `navbar` requirement is specific to the theme that i'm using: https://kaiiiz.github.io/hugo-theme-monochrome/

### new issue: about now appears in recent posts on the home page, but not in the posts section list itself.

how do I remove the about page from recent posts and the posts section?