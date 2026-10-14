
---
layout: default
title: Home
description: My software engineering portfolio, projects and experiences.
---

<section class="hero">
  <p class="eyebrow"><span class="status-dot"></span> SOFTWARE ENGINEERING · PORTFOLIO</p>
  <h1>Building things.<br>Learning constantly.<br><span>Sharing the process.</span></h1>
  <p class="hero-description">
    I'm Tristan, a software engineering student interested in building useful
    software, exploring new technologies, and continuously improving my skills.
    This is where I document the journey.
  </p>
  <div class="hero-actions">
    <a class="button button-primary" href="#journal">Explore my work ↓</a>
    <a class="button button-secondary" href="{{ '/about/' | relative_url }}">About me ↗</a>
  </div>
  <div class="hero-meta">
    <span><span class="status-dot"></span> OPEN TO LEARNING & COLLABORATION</span>
    <span>BASED IN BELGIUM</span>
  </div>
</section>

<section class="section projects-intro">
  <div class="section-label">01 / WHAT I DO</div>
  <div class="intro-content">
    <h2>Code, projects<br>and experiences.</h2>
    <p>
      From software projects and technical experiments to conferences,
      coursework and professional experiences, this portfolio documents
      what I build, what I learn and how I approach problems.
    </p>
    <a class="text-link" href="{{ '/projects/' | relative_url }}">Explore my projects ↗</a>
  </div>
</section>

<section class="section journal-section" id="journal">
  <div class="section-heading">
    <div>
      <p class="eyebrow">02 / THE JOURNAL</p>
      <h2>Notes from the journey<span class="heading-dot">.</span></h2>
    </div>
    <span class="muted-label">{{ site.posts | size }} ENTRIES</span>
  </div>

  <div class="journal-tools">
    <label class="search-box">
      <span aria-hidden="true">⌕</span>
      <input id="post-search" type="search" placeholder="Search projects, events, topics..." aria-label="Search journal posts">
    </label>
    <span class="muted-label">NEWEST FIRST ↓</span>
  </div>

  <div class="post-list" id="post-list">
    {% for post in site.posts %}
      <article class="post-card"
        data-search="{{ post.title | escape }} {{ post.categories | join: ' ' | escape }} {{ post.excerpt | strip_html | escape }}">
        <time class="post-date" datetime="{{ post.date | date_to_xmlschema }}">
          <span class="date-day">{{ post.date | date: "%d" }}</span>
          <span class="date-month">{{ post.date | date: "%b %Y" | upcase }}</span>
        </time>
        <div class="post-content">
          <div class="post-categories">
            {% for category in post.categories %}
              <span>{{ category }}</span>
            {% endfor %}
          </div>
          <h3><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></h3>
          <p>{{ post.excerpt | strip_html | strip_newlines | truncate: 190 }}</p>
          <a class="read-link" href="{{ post.url | relative_url }}">READ ENTRY <span>↗</span></a>
        </div>
        <a class="post-arrow" href="{{ post.url | relative_url }}" aria-label="Read {{ post.title | escape }}">↗</a>
      </article>
    {% endfor %}
  </div>

  <p id="no-results" class="empty-state" hidden>No entries found. Try another search.</p>
</section>

<section class="closing-banner">
  <div>
    <p class="eyebrow">ALWAYS BUILDING</p>
    <h2>The next chapter<br>starts here.</h2>
  </div>
  <a class="button button-primary" href="{{ '/about/' | relative_url }}">More about me ↗</a>
</section>

<script>
  const searchInput = document.getElementById("post-search");
  const postCards = document.querySelectorAll(".post-card");
  const noResults = document.getElementById("no-results");

  searchInput.addEventListener("input", () => {
    const query = searchInput.value.toLowerCase().trim();
    let visibleCount = 0;

    postCards.forEach(card => {
      const matches = card.dataset.search.toLowerCase().includes(query);
      card.hidden = !matches;
      if (matches) visibleCount++;
    });

    noResults.hidden = visibleCount !== 0;
  });
</script>
