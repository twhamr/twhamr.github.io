---
layout: default
title: Blog
permalink: /blog/
---

<section
  class="taxonomy-page"
  data-taxonomy-page
  data-page-size="6"
  data-item-label="post"
  data-item-label-plural="posts"
>
  <header class="taxonomy-header">
    <h1>{{ page.title }}</h1>
    <p class="taxonomy-intro">
      Notes, write-ups, and project updates across networking, software development, and cybersecurity.
    </p>
  </header>

  <div class="taxonomy-controls">
    <div class="taxonomy-filter" data-taxonomy-filter></div>
    <p class="taxonomy-status" data-taxonomy-status></p>
  </div>

  <div class="taxonomy-list" data-taxonomy-list>
    {% for post in site.posts %}
      <article class="taxonomy-card" data-terms='{{ post.tags | jsonify }}'>
        <div class="taxonomy-meta">
          <span class="taxonomy-date">
            {{ post.date | date: "%b %-d, %Y" }}
          </span>

          {% if post.tags and post.tags.size > 0 %}
            <span class="taxonomy-badges">
              {% for tag in post.tags %}
                <span class="taxonomy-badge">{{ tag }}</span>
              {% endfor %}
            </span>
          {% endif %}
        </div>

        <h2 class="taxonomy-title">
          <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        </h2>

        {% if post.excerpt %}
          <p class="taxonomy-excerpt">
            {{ post.excerpt | strip_html | truncate: 180 }}
          </p>
        {% endif %}

        <a class="taxonomy-link" href="{{ post.url | relative_url }}">
          Read more →
        </a>
      </article>
    {% endfor %}
  </div>

  <div class="taxonomy-actions">
    <button class="taxonomy-button" type="button" data-taxonomy-load-more>
      Load more
    </button>
  </div>

  <p class="taxonomy-empty hidden" data-taxonomy-empty>
    No posts match this filter.
  </p>
</section>

<script>
document.addEventListener('DOMContentLoaded', function () {
  document.querySelectorAll('[data-taxonomy-page]').forEach(function (section) {
    const pageSize = parseInt(section.dataset.pageSize || '6', 10);
    const itemLabel = section.dataset.itemLabel || 'item';
    const itemLabelPlural = section.dataset.itemLabelPlural || (itemLabel + 's');

    const filterContainer = section.querySelector('[data-taxonomy-filter]');
    const status = section.querySelector('[data-taxonomy-status]');
    const empty = section.querySelector('[data-taxonomy-empty]');
    const loadMore = section.querySelector('[data-taxonomy-load-more]');
    const cards = Array.from(section.querySelectorAll('.taxonomy-card'));

    let activeTerm = 'all';
    let visibleLimit = pageSize;

    function slugifyTag(value) {
      return String(value)
        .toLowerCase()
        .trim()
        .replace(/[^a-z0-9]+/g, '-')
        .replace(/^-+|-+$/g, '');
    }

    function prettyLabel(value) {
      return String(value)
        .replace(/-/g, ' ')
        .replace(/\b\w/g, function (m) { return m.toUpperCase(); });
    }

    function getTerms(card) {
      try {
        const raw = JSON.parse(card.dataset.terms || '[]');
        return raw.map(slugifyTag);
      } catch (e) {
        return [];
      }
    }

    function buildFilters() {
      const counts = new Map();

      cards.forEach(function (card) {
        getTerms(card).forEach(function (term) {
          counts.set(term, (counts.get(term) || 0) + 1);
        });
      });

      filterContainer.innerHTML = '';

      const allButton = document.createElement('button');
      allButton.type = 'button';
      allButton.className = 'taxonomy-chip is-active';
      allButton.dataset.filterTerm = 'all';
      allButton.textContent = 'All';
      filterContainer.appendChild(allButton);

      Array.from(counts.keys()).sort().forEach(function (term) {
        const button = document.createElement('button');
        button.type = 'button';
        button.className = 'taxonomy-chip';
        button.dataset.filterTerm = term;
        button.textContent = prettyLabel(term) + ' (' + counts.get(term) + ')';
        filterContainer.appendChild(button);
      });

      filterContainer.querySelectorAll('[data-filter-term]').forEach(function (button) {
        button.addEventListener('click', function () {
          filterContainer.querySelectorAll('[data-filter-term]').forEach(function (b) {
            b.classList.remove('is-active');
          });

          button.classList.add('is-active');
          activeTerm = button.dataset.filterTerm || 'all';
          visibleLimit = pageSize;
          render();
        });
      });
    }

    function matches(card) {
      return activeTerm === 'all' || getTerms(card).includes(activeTerm);
    }

    function render() {
      let matched = 0;
      let shown = 0;

      cards.forEach(function (card) {
        const isMatch = matches(card);

        if (!isMatch) {
          card.classList.add('hidden');
          return;
        }

        matched += 1;

        const shouldShow = shown < visibleLimit;
        card.classList.toggle('hidden', !shouldShow);

        if (shouldShow) {
          shown += 1;
        }
      });

      empty.classList.toggle('hidden', matched !== 0);
      loadMore.classList.toggle('hidden', matched === 0 || shown >= matched);

      const label = activeTerm === 'all' ? 'all ' + itemLabelPlural : prettyLabel(activeTerm);

      status.textContent =
        matched === 0
          ? 'Showing 0 of 0 ' + itemLabelPlural + '.'
          : 'Showing ' +
            Math.min(shown, matched) +
            ' of ' +
            matched +
            ' ' +
            itemLabelPlural +
            (activeTerm === 'all' ? '' : ' tagged ' + label) +
            '.';
    }

    loadMore.addEventListener('click', function () {
      visibleLimit += pageSize;
      render();
    });

    buildFilters();
    render();
  });
});
</script>