---
layout: default
title: Home
---

# Welcome to My Website!

In this website, you’ll find notes from my cybersecurity journey: CTF writeups,
research, blog posts, and other experiments I’m willing to share.

---

# Latest Posts

{% if site.posts and site.posts.size > 0 %}
  {% assign latest_post = site.posts | first %}
  <p><em>Last Update: {{ latest_post.date | date: "%B %-d, %Y" }} (UTC)</em></p>

  {% comment %}
  Group posts by their `category` field. For this to work,
  each post should have a single `category:` in its front matter,
  like `category: Writeups` or `category: Research`.
  {% endcomment %}

  {% assign posts_by_category = site.posts | group_by: "category" %}

  {% for group in posts_by_category %}
  <h3>&gt; {{ group.name }}</h3>
  <ul>
    {% for post in group.items limit:5 %}
      <li>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>,
        {{ post.date | date: "%B %-d, %Y" }}
      </li>
    {% endfor %}
  </ul>
  {% endfor %}

{% else %}
  <p>No posts yet. Once you publish your first post, they’ll show up here.</p>
{% endif %}
