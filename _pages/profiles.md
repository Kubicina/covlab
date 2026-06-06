---
layout: profiles
permalink: /people/
title: people
description: >
  Members of the CoVLab — Computational and Virology Laboratory at Comenius University in Bratislava.
nav: true
nav_order: 4

# The `profiles` layout renders one featured card per entry below.
# Each card pulls a photo from assets/img/ and renders the referenced content file as the bio text.
# For the full roster (all groups), see the Liquid section in the page body below.
profiles:
  - align: left
    image: people/placeholder.jpg
    content: people_pi_placeholder.md
    image_circular: false
    more_info: >
      <p>Department of Molecular Biology</p>
      <p>Faculty of Natural Sciences</p>
      <p>Comenius University, Bratislava</p>
---

<!-- _pages/profiles.md -->
<!--
  The featured profile card above is rendered by the `profiles` layout (al_folio_core gem).
  The sections below iterate over _data/people.yml to list all lab members by group.
  To add or update a person, edit _data/people.yml — no changes to this file are needed.
-->

{% assign groups = "principal_investigators,researchers,phd_students,master_students" | split: "," %}
{% assign group_labels = "Principal Investigators,Researchers & Postdocs,PhD Students,Master Students" | split: "," %}

{% assign active_members = site.data.people | where: "active", true %}

{% for i in (0..3) %}
{% assign group_key = groups[i] %}
{% assign group_label = group_labels[i] %}
{% assign group_members = active_members | where: "group", group_key %}
{% if group_members.size > 0 %}

## {{ group_label }}

<div class="row row-cols-1 row-cols-md-2 row-cols-lg-3 g-4 mb-5">
  {% for person in group_members %}
  <div class="col">
    <div class="card h-100 shadow-sm">
      <img
        src="{{ '/assets/img/people/' | append: person.image | relative_url }}"
        class="card-img-top"
        alt="Photo of {{ person.name }}"
        style="object-fit: cover; height: 220px;"
      />
      <div class="card-body">
        <h5 class="card-title mb-1">{{ person.title }} {{ person.name }}</h5>
        <p class="card-subtitle text-muted mb-2" style="font-size: 0.875rem;">{{ person.role }}</p>
        {% if person.expertise %}
        <ul class="list-unstyled mb-2" style="font-size: 0.85rem;">
          {% for interest in person.expertise %}
          <li>&#x2022; {{ interest }}</li>
          {% endfor %}
        </ul>
        {% endif %}
      </div>
      {% if person.email or person.orcid or person.scholar or person.website %}
      <div class="card-footer bg-transparent border-top-0" style="font-size: 0.8rem;">
        {% if person.email %}
          <a href="mailto:{{ person.email }}" title="Email" class="me-2"><i class="fas fa-envelope"></i></a>
        {% endif %}
        {% if person.orcid %}
          <a href="https://orcid.org/{{ person.orcid }}" title="ORCID" target="_blank" rel="noopener noreferrer" class="me-2"><i class="ai ai-orcid"></i></a>
        {% endif %}
        {% if person.scholar %}
          <a href="{{ person.scholar }}" title="Google Scholar" target="_blank" rel="noopener noreferrer" class="me-2"><i class="ai ai-google-scholar"></i></a>
        {% endif %}
        {% if person.website %}
          <a href="{{ person.website }}" title="Website" target="_blank" rel="noopener noreferrer"><i class="fas fa-globe"></i></a>
        {% endif %}
      </div>
      {% endif %}
    </div>
  </div>
  {% endfor %}
</div>

{% endif %}
{% endfor %}

{% assign alumni = site.data.people | where: "active", false %}
{% if alumni.size > 0 %}

## Alumni

<div class="row row-cols-1 row-cols-md-3 row-cols-lg-4 g-3 mb-5">
  {% for person in alumni %}
  <div class="col">
    <div class="card h-100 shadow-sm">
      <div class="card-body">
        <h6 class="card-title mb-0">{{ person.title }} {{ person.name }}</h6>
        <p class="card-subtitle text-muted" style="font-size: 0.8rem;">{{ person.role }}</p>
      </div>
    </div>
  </div>
  {% endfor %}
</div>

{% endif %}
