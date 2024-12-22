---
layout: page
permalink: /repositories/
title: Github Repositories
description:  My GitHub profile, statistics, and top repositories.
nav: true
nav_order: 5
---

{% if site.data.repositories.github_users %}

## GitHub Statistics

<div class="repositories d-flex flex-wrap flex-md-row flex-column align-items-center">
  {% for user in site.data.repositories.github_users %}
    {% include repository/repo_user.liquid username=user %}
  {% endfor %}
</div>

<br>

{% if site.repo_trophies.enabled %}
{% for user in site.data.repositories.github_users %}
{% if site.data.repositories.github_users.size > 1 %}

  <h4>{{ user }}</h4>
  {% endif %}
  <div class="repositories d-flex flex-wrap flex-md-row flex-column align-items-center">
  {% include repository/repo_trophies.liquid username=user %}
  </div>

<br>

{% endfor %}
{% endif %}
{% endif %}

{% if site.data.repositories.github_repos %}

## Top Repositories

<div class="repositories d-flex flex-wrap flex-md-row flex-column align-items-center">
  {% for repo in site.data.repositories.github_repos %}
    {% include repository/repo.liquid repository=repo %}
  {% endfor %}
</div>
{% endif %}
