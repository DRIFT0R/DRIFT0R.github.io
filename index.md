---
layout: default
title: Home
---

<div class="terminal-panel">
  <div class="terminal-title">
    # Welcome to My Website!
  </div>
  <div class="terminal-body">
    <p>
      This website is a fragment of my ethical hacking and cybersecurity journey. You'll find projects, essays, CTF writeups, blogs and other cool things and thoughts I want to share. 
</p>
  </div>
</div>

---

<div class="terminal-panel">
  <div class="terminal-title">
    # Latest Posts
  </div>
  <div class="terminal-body">
    {% if site.posts and site.posts.size > 0 %}
      {% assign latest_post = site.posts | first %}
      <p class="terminal-meta">
        Last Update: {{ latest_post.date | date: "%B %-d, %Y" }} (UTC)
      </p>
  {% comment %}
  Group posts by their `category` field. For this to work,
  each post should have a single `category:` in its front matter,
  like `category: Writeups` or `category: Research`.
  {% endcomment %}

  {% assign posts_by_category = site.posts | group_by: "category" %}

      {% for group in posts_by_category %}
        <div class="category-block">
          <h3 class="category-heading">&gt; {{ group.name | default: "Uncategorized" }}</h3>
          <ul class="post-list">
            {% for post in group.items limit:5 %}
              <li class="post-list-item">
                <a class="post-link" href="{{ post.url | relative_url }}">
                  {{ post.title }}
                </a>
                <span class="post-date">
                  {{ post.date | date: "%B %-d, %Y" }}
                </span>
              </li>
            {% endfor %}
          </ul>
        </div>
      {% endfor %}
    {% else %}
      <p class="terminal-meta">
        No posts yet. Once you publish your first post, they’ll show up here.
      </p>
    {% endif %}
  </div>
</div>
