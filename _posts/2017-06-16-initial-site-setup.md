---
layout: post
title: A Github Page Setup
categories: []
tags: [github-pages]
description:
comments: true
---

[GitHub Pages](https://pages.github.com/) is a web hosting service offered by [GitHub](https://github.com/) for hosting static web pages for GitHub users, user blogs, project documentation, or even whole books.
It is integrated with the [Jekyll](https://jekyllrb.com/) software for static web site and blog generation. The Jekyll source pages for a web site can be stored on GitHub as a Git repository, and when the repository is updated the GitHub Pages servers will automatically regenerate the site.
GitHub Pages was launched in late 2008. As with the rest of GitHub, it includes both free and paid tiers of service, instead of being supported by web advertising. Web sites generated through this service are hosted either as subdomains of the github.io domain, or as custom domains bought through a third-party domain name registrar.

Steps for setup:
* Fork this repository.
* Update repository name to `<user_name>.github.io`.
* Customize `_config.yml` to match user credentials.
* In `_includes/comments.html` edit `disqus_shortname`.
* Update `index.html` bio.
* Commit the changes.
* Done!


This site is build on top of the customizations by [psteadman](https://github.com/psteadman) on [lanyon](https://github.com/poole/lanyon) theme which derives from [poole](https://github.com/poole).
Head over to the post [Using Jekyll, Poole and Lanyon to setup my github user page](http://patricksteadman.ca/2014/08/04/lanyonsetup/) for further references.

## REFERENCES:

<small>[Github Pages - Wikipedia](https://en.wikipedia.org/wiki/GitHub_Pages)</small>

<small>[Using Jekyll, Poole and Lanyon to setup my github user page](http://patricksteadman.ca/2014/08/04/lanyonsetup/)</small>
