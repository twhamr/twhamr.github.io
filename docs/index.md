---
layout: default
title: Home
---

<section class="home-page taxonomy-page">

  <!-- Intro / Hero -->
  <section class="home-hero">
    <div class="home-hero-content">

      <div class="home-headshot">
        <!-- Replace with your image -->
        <img src="/assets/images/headshot.jpg" alt="Your Name">
      </div>

      <div class="home-intro">
        <h1 class="home-name">Your Name</h1>
        <p class="home-title">Networking | Software Development | Cybersecurity</p>

        <p class="taxonomy-intro home-description">
          I am a student and aspiring technologist with a focus on networking, software development, and cybersecurity.
          I enjoy building projects, learning through hands-on experience, and sharing what I learn through writing.
        </p>

        <div class="home-actions">
          <a class="taxonomy-button" href="https://github.com/{{ site.github_username }}" target="_blank"><i class="bi bi-github"></i> GitHub</a>
          <a class="taxonomy-button" href="https://linkedin.com/in/{{ site.linkedin_username }}" target="_blank"><i class="bi bi-linkedin"></i> LinkedIn</a>
        </div>

      </div>
    </div>
  </section>

  <!-- Quick Links -->
  <section class="home-section">
    <h2 class="experience-section-title">Explore</h2>

    <div class="home-grid">
      <a class="taxonomy-card home-card" href="/projects/">
        <h3 class="taxonomy-title">Projects</h3>
        <p class="taxonomy-excerpt">Hands-on work across networking, development, and security.</p>
      </a>

      <a class="taxonomy-card home-card" href="/blog/">
        <h3 class="taxonomy-title">Blog</h3>
        <p class="taxonomy-excerpt">Write-ups, notes, and technical insights.</p>
      </a>

      <a class="taxonomy-card home-card" href="/experience/">
        <h3 class="taxonomy-title">Experience</h3>
        <p class="taxonomy-excerpt">Work history, education, and certifications.</p>
      </a>
    </div>
  </section>

  <!-- Recent Blog Posts -->
  <section class="home-section">
    <h2 class="experience-section-title">Latest Posts</h2>

    <div class="taxonomy-list">
      {% for post in site.posts limit:3 %}
        <article class="taxonomy-card">
          <div class="taxonomy-meta">
            <span class="taxonomy-date">{{ post.date | date: "%b %-d, %Y" }}</span>
          </div>

          <h3 class="taxonomy-title">
            <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
          </h3>

          {% if post.excerpt %}
            <p class="taxonomy-excerpt">
              {{ post.excerpt | strip_html | truncate: 120 }}
            </p>
          {% endif %}

          <a class="taxonomy-link" href="{{ post.url | relative_url }}">Read more →</a>
        </article>
      {% endfor %}
    </div>

    <p class="home-more-link">
      <a class="taxonomy-link" href="/blog/">View all posts →</a>
    </p>
  </section>

  <!-- Featured Projects -->
  <section class="home-section">
    <h2 class="experience-section-title">Projects</h2>

    <div class="taxonomy-list">
      {% for project in site.projects limit:3 %}
        <article class="taxonomy-card">
          <h3 class="taxonomy-title">
            <a href="{{ project.url | relative_url }}">{{ project.title }}</a>
          </h3>

          {% if project.excerpt %}
            <p class="taxonomy-excerpt">
              {{ project.excerpt | strip_html | truncate: 120 }}
            </p>
          {% endif %}

          <a class="taxonomy-link" href="{{ project.url | relative_url }}">View project →</a>
        </article>
      {% endfor %}
    </div>

    <p class="home-more-link">
      <a class="taxonomy-link" href="/projects/">View all projects →</a>
    </p>
  </section>

</section>