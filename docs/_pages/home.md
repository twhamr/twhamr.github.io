---
layout: home
title: Home
permalink: /
---

<div class="text-center">
    <img src="{{ '/static/images/temp-avatar.png' | relative_url }}" alt="temporary avatar image">
    <h2>{{ site.owner.name }}</h2>
    <p>{{ site.owner.bio }}</p>
    <p><strong>Contact: </strong> {{ site.owner.email }} </p>
</div>

{% include social.html %}