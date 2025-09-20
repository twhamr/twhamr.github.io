---
layout: home
title: Home
permalink: /
---

<div class="text-center">
    <img style="width: 500px; height: 500px; border-radius: 50%;" src="{{ '/static/images/avatar.jpg' | relative_url }}" alt="Tyler Hamrick">
    <h2>{{ site.owner.name }}</h2>
    <p>{{ site.owner.bio }}</p>
    <p><strong>Contact: </strong> {{ site.owner.email }} </p>
</div>

{% include social.html %}