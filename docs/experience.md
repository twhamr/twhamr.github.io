---
layout: default
title: Experience
permalink: /experience/
---

<section class="experience-page taxonomy-page">
  <header class="taxonomy-header experience-header">
    <h1>{{ page.title }}</h1>
    <p class="taxonomy-intro">
      Work experience, education, certifications, and the areas I have been building in across networking, software development, and cybersecurity.
    </p>
  </header>

  <section class="experience-focus">
    <h2 class="experience-section-title">Core Focus Areas</h2>
    <div class="experience-focus-chips">
      <span class="taxonomy-badge">Networking</span>
      <span class="taxonomy-badge">Software Development</span>
      <span class="taxonomy-badge">Cybersecurity</span>
    </div>
  </section>

  {% if site.data.experiences and site.data.experiences.size > 0 %}
    <section class="experience-section">
      <h2 class="experience-section-title">Work Experience</h2>

      <div class="experience-list">
        {% for experience_pair in site.data.experiences %}
          {% assign experience = experience_pair[1] %}

          <article class="experience-card">
            <div class="experience-card-header">
              <div>
                <h3 class="experience-title">{{ experience.role }}</h3>
                <p class="experience-company">
                  {{ experience.company }}
                  {% if experience.location %}
                    <span class="experience-separator">•</span> {{ experience.location }}
                  {% endif %}
                </p>
              </div>

              {% if experience.period %}
                <p class="experience-period">{{ experience.period }}</p>
              {% endif %}
            </div>

            {% if experience.summary %}
              <p class="experience-summary">{{ experience.summary }}</p>
            {% endif %}

            {% if experience.highlights and experience.highlights.size > 0 %}
              <ul class="experience-highlights">
                {% for highlight in experience.highlights %}
                  <li>{{ highlight }}</li>
                {% endfor %}
              </ul>
            {% endif %}

            {% if experience.skills and experience.skills.size > 0 %}
              <div class="taxonomy-badges experience-badges">
                {% for skill in experience.skills %}
                  <span class="taxonomy-badge">{{ skill }}</span>
                {% endfor %}
              </div>
            {% endif %}

            {% if experience.link %}
              <a class="taxonomy-link experience-link" href="{{ experience.link }}" target="_blank" rel="noopener">
                View more ↗
              </a>
            {% endif %}
          </article>
        {% endfor %}
      </div>
    </section>
  {% endif %}

  {% if site.data.education and site.data.education.size > 0 %}
    <section class="experience-section">
      <h2 class="experience-section-title">Education</h2>

      <div class="experience-list">
        {% for edu_pair in site.data.education %}
          {% assign edu = edu_pair[1] %}

          <article class="experience-card">
            <div class="experience-card-header">
              <div>
                <h3 class="experience-title">{{ edu.degree }}</h3>
                <p class="experience-company">
                  {{ edu.institution }}
                  {% if edu.location %}
                    <span class="experience-separator">•</span> {{ edu.location }}
                  {% endif %}
                </p>
              </div>

              {% if edu.period %}
                <p class="experience-period">{{ edu.period }}</p>
              {% endif %}
            </div>

            {% if edu.summary %}
              <p class="experience-summary">{{ edu.summary }}</p>
            {% endif %}

            {% if edu.highlights and edu.highlights.size > 0 %}
              <ul class="experience-highlights">
                {% for highlight in edu.highlights %}
                  <li>{{ highlight }}</li>
                {% endfor %}
              </ul>
            {% endif %}

            {% if edu.skills and edu.skills.size > 0 %}
              <div class="taxonomy-badges experience-badges">
                {% for skill in edu.skills %}
                  <span class="taxonomy-badge">{{ skill }}</span>
                {% endfor %}
              </div>
            {% endif %}
          </article>
        {% endfor %}
      </div>
    </section>
  {% endif %}

  {% if site.data.certifications and site.data.certifications.size > 0 %}
    <section class="experience-section">
      <h2 class="experience-section-title">Certifications</h2>

      <div class="cert-list">
        {% for cert_pair in site.data.certifications %}
          {% assign cert = cert_pair[1] %}

          <article class="cert-card">
            <div class="cert-card-header">
              <div>
                <h3 class="experience-title">{{ cert.name }}</h3>
                <p class="experience-company">{{ cert.issuer }}</p>
              </div>

              {% if cert.date %}
                <p class="experience-period">{{ cert.date }}</p>
              {% endif %}
            </div>

            {% if cert.summary %}
              <p class="experience-summary">{{ cert.summary }}</p>
            {% endif %}

            {% if cert.skills and cert.skills.size > 0 %}
              <div class="taxonomy-badges experience-badges">
                {% for skill in cert.skills %}
                  <span class="taxonomy-badge">{{ skill }}</span>
                {% endfor %}
              </div>
            {% endif %}

            {% if cert.credential_url %}
              <a class="taxonomy-link experience-link" href="{{ cert.credential_url }}" target="_blank" rel="noopener">
                Credential ↗
              </a>
            {% endif %}
          </article>
        {% endfor %}
      </div>
    </section>
  {% endif %}
</section>