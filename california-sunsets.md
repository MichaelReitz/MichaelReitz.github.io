---
title: "California Sunsets"
layout: default
---

# California Sunsets

Here I keep a gallery of sunsets, most of them captured along the Southern California coastline in and around San Diego. Some of these evenings also coincide with my attempts to learn how to surf. While these photographs may not live up to high photographic standards, I enjoy capturing the diversity of sunsets and the different colors they create.

<style>
.slideshow-container {
  position: relative;
  max-width: 700px;
  margin: 28px auto 0;
  user-select: none;
}
.slide {
  display: none;
  text-align: center;
}
.slide.active {
  display: block;
}
.slide img {
  width: 100%;
  max-height: 520px;
  object-fit: contain;
  border-radius: 8px;
  background: #111;
}
.slide-counter {
  text-align: center;
  margin-top: 8px;
  font-size: 0.85em;
  color: #888;
}
.slide-nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 10px;
}
.slide-btn {
  background: none;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 6px 18px;
  font-size: 1.1em;
  cursor: pointer;
  color: inherit;
  transition: background 0.15s;
}
.slide-btn:hover {
  background: rgba(0,0,0,0.08);
}
.dot-row {
  display: flex;
  gap: 6px;
  flex-wrap: wrap;
  justify-content: center;
}
.dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #ccc;
  cursor: pointer;
  transition: background 0.15s;
}
.dot.active {
  background: #555;
}
</style>

<div class="slideshow-container">
  <div class="slide active"><img src="images/532f9338-fad8-46bb-9d3a-67615f524555.JPG" alt="California sunset 1"></div>
  <div class="slide"><img src="images/IMG_1780.jpg" alt="California sunset 2"></div>
  <div class="slide"><img src="images/IMG_2344.jpg" alt="California sunset 3"></div>
  <div class="slide"><img src="images/IMG_4800.jpg" alt="California sunset 4"></div>
  <div class="slide"><img src="images/IMG_4840.jpg" alt="California sunset 5"></div>
  <div class="slide"><img src="images/IMG_4959.jpg" alt="California sunset 6"></div>
  <div class="slide"><img src="images/IMG_4996.jpg" alt="California sunset 7"></div>
  <div class="slide"><img src="images/IMG_6086.jpg" alt="California sunset 8"></div>
  <div class="slide"><img src="images/IMG_6251.jpg" alt="California sunset 9"></div>
  <div class="slide"><img src="images/IMG_6294_2.jpg" alt="California sunset 10"></div>
  <div class="slide"><img src="images/IMG_6447.jpg" alt="California sunset 11"></div>
  <div class="slide"><img src="images/IMG_6448.jpg" alt="California sunset 12"></div>
  <div class="slide"><img src="images/IMG_7637.jpg" alt="California sunset 13"></div>

  <p class="slide-counter"><span id="current">1</span> / <span id="total"></span></p>

  <div class="slide-nav">
    <button class="slide-btn" id="prev">&#8592; Prev</button>
    <div class="dot-row" id="dots"></div>
    <button class="slide-btn" id="next">Next &#8594;</button>
  </div>
</div>

<script>
(function () {
  var slides = document.querySelectorAll('.slide');
  var dots   = document.getElementById('dots');
  var cur    = document.getElementById('current');
  var tot    = document.getElementById('total');
  var idx    = 0;

  tot.textContent = slides.length;

  slides.forEach(function (_, i) {
    var d = document.createElement('span');
    d.className = 'dot' + (i === 0 ? ' active' : '');
    d.addEventListener('click', function () { go(i); });
    dots.appendChild(d);
  });

  function go(n) {
    slides[idx].classList.remove('active');
    dots.children[idx].classList.remove('active');
    idx = (n + slides.length) % slides.length;
    slides[idx].classList.add('active');
    dots.children[idx].classList.add('active');
    cur.textContent = idx + 1;
  }

  document.getElementById('prev').addEventListener('click', function () { go(idx - 1); });
  document.getElementById('next').addEventListener('click', function () { go(idx + 1); });

  document.addEventListener('keydown', function (e) {
    if (e.key === 'ArrowRight') go(idx + 1);
    if (e.key === 'ArrowLeft')  go(idx - 1);
  });
})();
</script>
