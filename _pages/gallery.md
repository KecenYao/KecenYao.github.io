---
permalink: /gallery/
title: "Travel Photo Gallery"
excerpt: "A collection of travel photos"
author_profile: false
---

## Travel Photo Gallery

Welcome to my travel photo gallery! Here are some of my favorite moments captured during my travels.

<style>
  .gallery-section {
    margin-bottom: 50px;
  }
  .gallery-title {
    text-align: center;
    font-size: 2em;
    margin-bottom: 20px;
    color: #2c3e50;
  }
  .gallery {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
  .gallery img {
    margin: 10px;
    border-radius: 10px;
    width: 300px;
    height: auto;
    transition: transform 0.2s, box-shadow 0.2s;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  }
  .gallery img:hover {
    transform: scale(1.05);
    box-shadow: 0 8px 16px rgba(0,0,0,0.2);
  }
</style>

{% assign places = "Shanghai, Tokyo, New York" | split: ", " %}

{% for place in places %}
  <div class="gallery-section">
    <h2 class="gallery-title">{{ place }}</h2>
    <div class="gallery">
      {% assign images = site.static_files | where: "path", "contains", "images/gallery/" | where: "path", "contains", place %}
      <!-- {% for image in images %}
        <div class="photo">
          <img src="{{ site.baseurl }}{{ image.path }}" alt="{{ image.basename | escape }}" loading="lazy">
        </div>
      {% endfor %} -->
    </div>
  </div>
{% endfor %}
