---
permalink: /gallery/
title: "Photo Gallery"
excerpt: "A collection of photos"
author_profile: false
---

## Photo Gallery

Welcome to my photo gallery! Here are some of my favorite moments captured in images. Click on any photo to view it in full size.

<style>
  .gallery {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
  }
  .gallery img {
    margin: 10px;
    border-radius: 10px;
    width: 300px; /* Adjust as needed */
    height: auto;
    transition: transform 0.2s;
  }
  .gallery img:hover {
    transform: scale(1.05);
  }
</style>

<div class="gallery">
    {% for image in site.static_files %}
        {% if image.path contains 'images/gallery/' %}
            <div class="photo">
                <img src="{{ site.baseurl }}{{ image.path }}" alt="{{ image.basename }}" loading="lazy">
            </div>
        {% endif %}
    {% endfor %}
</div>
