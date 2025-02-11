---
layout: page
title: Projects
permalink: /projects/
---

{% assign all_projects = site.data.projects %}

This is an empty page that will contain all my projects. They will be separated by personal and course-related projects.

<div class="projects-school">
    <h3>School</h3>
    <div class="project-wrapper">
        <ul class="project-list">
            {% for project in all_projects.school %}
                <li class="project-site">{{ project }}</li>
            {% endfor %}
        </ul>
    </div>
</div>

<div class="projects-personal">
    <h3>Personal</h3>
    <div class="project-wrapper">
        <ul class="project-list">
            {% for project in all_projects.personal %}
                <li class="project-site">{{ project }}</li>
            {% endfor %}
        </ul>
    </div>
</div>