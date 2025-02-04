---
layout: home
title: Home
permalink: /
---

<div id="avatar">
    <img class="avatar-img" src="{{ '/static/images/temp-avatar.png' | relative_url }}" alt="temporary avatar image">
    <h2 class="avatar-name">{{ site.owner.name }}</h2>
    <p class="avatar-bio">{{ site.owner.bio }}</p>
    <p class="avatar-email"><strong>Contact: </strong> {{ site.owner.email }} </p>
</div>

{% include social.html %}