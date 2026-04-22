---
layout: default
title: Blog
permalink: /blog/
---

{% include taxonomy-index.html
  title=page.title
  intro="Notes, write-ups, and project updates across networking, software development, and cybersecurity."
  items=site.posts
  terms_key="tags"
  date_key="date"
  title_key="title"
  excerpt_key="excerpt"
  item_label="post"
  item_label_plural="posts"
  empty_text="No posts match this tag."
  load_more_text="Load more"
  link_text="Read more →"
  page_size=6
%}