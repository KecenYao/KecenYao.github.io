---
permalink: /map-gallery
title: "Map-Based Photo Gallery"
excerpt: "A map with clickable points to view photo galleries"
author_profile: false
---

## Map-Based Photo Gallery

Welcome to the map-based photo gallery! Click on a point on the map to view the associated photo gallery.

<style>
  #map {
    height: 600px;
    width: 100%;
  }
  .gallery {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    margin-top: 20px;
  }
  .gallery img {
    margin: 10px;
    border-radius: 10px;
    width: 100px; /* Adjust as needed */
    height: auto;
    transition: transform 0.2s;
  }
  .gallery img:hover {
    transform: scale(1.05);
  }
</style>

<div id="map"></div>
<div id="gallery" class="gallery" style="display:none;"></div>

<script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
<script>
  // Initialize the map
  var map = L.map('map').setView([51.505, -0.09], 13);

  // Add a tile layer to the map
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
  }).addTo(map);

  // Example points with associated images
  var points = [
    {
      coords: [51.505, -0.09],
      images: [
        {% for image in site.static_files %}
          {% if image.path contains 'images/gallery/location1/' %}
            '{{ site.baseurl }}{{ image.path }}',
          {% endif %}
        {% endfor %}
      ]
    },
    {
      coords: [51.515, -0.1],
      images: [
        {% for image in site.static_files %}
          {% if image.path contains 'images/gallery/location2/' %}
            '{{ site.baseurl }}{{ image.path }}',
          {% endif %}
        {% endfor %}
      ]
    }
  ];

  // Add markers to the map
  points.forEach(function(point) {
    var marker = L.marker(point.coords).addTo(map);
    marker.on('click', function() {
      showGallery(point.images);
    });
  });

  // Function to display the gallery
  function showGallery(images) {
    var gallery = document.getElementById('gallery');
    gallery.innerHTML = '';
    images.forEach(function(image) {
      var img = document.createElement('img');
      img.src = image;
      img.alt = 'Photo';
      gallery.appendChild(img);
    });
    gallery.style.display = 'flex';
  }
</script>
