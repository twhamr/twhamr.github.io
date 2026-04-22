---
layout: default
title: Projects
permalink: /projects/
---

{% include taxonomy-index.html
  title=page.title
  intro="A collection of projects, labs, and builds focused on networking, software development, and cybersecurity."
  items=site.projects
  terms_key="skills"
  date_key="date"
  title_key="title"
  excerpt_key="excerpt"
  item_label="project"
  item_label_plural="projects"
  empty_text="No projects match this filter."
  load_more_text="Load more"
  link_text="View project →"
  page_size=6
%}