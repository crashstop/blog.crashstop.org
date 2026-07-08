# blog.crashstop.org
Updates and blog stuff for crashstop.org

Jekyll site. The home page renders every post in `_posts/` in full, newest first.

## Developing

Requires a modern Ruby (Homebrew's `ruby` works; system Ruby 2.6 does not).

```sh
bundle install    # gems go to vendor/bundle (see .bundle/config)
./serve           # dev server at http://localhost:2157, optional arg is the port
```

`bundle exec jekyll build` writes the static site to `_site/`.

## Writing posts

Add a Markdown file to `_posts/` named `YYYY-MM-DD-slug.md` with front matter:

```yaml
---
layout: post
title: "Post title"
---
```
