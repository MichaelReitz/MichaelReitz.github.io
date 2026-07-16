---
title: "California Sunsets"
layout: default
---

# California Sunsets

Here I keep a gallery of sunsets, most of them captured along the Southern California coastline in and around San Diego. Some of these evenings also coincide with my attempts of learning how to surf. While these photographs may not live up to high photographic standards, I enjoy capturing the diversity of sunsets and the different colors they create.

<style>
.ss-wrap {
  position: relative;
  max-width: 680px;
  margin: 28px auto 0;
  user-select: none;
}
.ss-viewport {
  width: 100%;
  overflow: hidden;
  border-radius: 8px;
  background: #111;
  position: relative;
}
.ss-track {
  display: flex;
  transition: transform 0.45s cubic-bezier(0.4, 0, 0.2, 1);
  will-change: transform;
}
.ss-track img {
  width: 100%;
  flex: 0 0 100%;
  height: 480px;
  object-fit: contain;
  display: block;
}
.ss-btn {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(255,255,255,0.85);
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  font-size: 1.2em;
  line-height: 1;
  cursor: pointer;
  z-index: 10;
  box-shadow: 0 1px 6px rgba(0,0,0,0.25);
  transition: background 0.15s;
  display: flex;
  align-items: center;
  justify-content: center;
}
.ss-btn:hover { background: rgba(255,255,255,1); }
.ss-btn.prev { left: 8px; }
.ss-btn.next { right: 8px; }
.ss-footer {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 12px;
  margin-top: 10px;
}
.ss-counter {
  font-size: 0.85em;
  color: #888;
  min-width: 48px;
  text-align: center;
}
.ss-dots {
  display: flex;
  gap: 6px;
  flex-wrap: wrap;
  justify-content: center;
}
.ss-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #ccc;
  cursor: pointer;
  border: none;
  padding: 0;
  transition: background 0.15s;
}
.ss-dot.active { background: #555; }
</style>

<div class="ss-wrap">
  <div class="ss-viewport">
    <div class="ss-track" id="ssTrack">
      <img src="images/532f9338-fad8-46bb-9d3a-67615f524555.JPG" alt="California sunset">
      <img src="images/IMG_1780.jpg"    alt="California sunset">
      <img src="images/IMG_2344.jpg"    alt="California sunset">
      <img src="images/IMG_4800.jpg"    alt="California sunset">
      <img src="images/IMG_4840.jpg"    alt="California sunset">
      <img src="images/IMG_4959.jpg"    alt="California sunset">
      <img src="images/IMG_4996.jpg"    alt="California sunset">
      <img src="images/IMG_6086.jpg"    alt="California sunset">
      <img src="images/IMG_6251.jpg"    alt="California sunset">
      <img src="images/IMG_6294_2.jpg"  alt="California sunset">
      <img src="images/IMG_6447.jpg"    alt="California sunset">
      <img src="images/IMG_6448.jpg"    alt="California sunset">
      <img src="images/IMG_7637.jpg"    alt="California sunset">
    </div>
  </div>
  <button class="ss-btn prev" id="ssPrev">&#8592;</button>
  <button class="ss-btn next" id="ssNext">&#8594;</button>
  <div class="ss-footer">
    <span class="ss-counter" id="ssCtr">1 / 13</span>
    <div class="ss-dots" id="ssDots"></div>
  </div>
</div>

<script>
(function () {
  var track  = document.getElementById('ssTrack');
  var dots   = document.getElementById('ssDots');
  var ctr    = document.getElementById('ssCtr');
  var imgs   = track.querySelectorAll('img');
  var n      = imgs.length;
  var idx    = 0;

  ctr.textContent = '1 / ' + n;

  for (var i = 0; i < n; i++) {
    var d = document.createElement('button');
    d.className = 'ss-dot' + (i === 0 ? ' active' : '');
    d.setAttribute('aria-label', 'Go to slide ' + (i + 1));
    (function (i) { d.addEventListener('click', function () { go(i); }); })(i);
    dots.appendChild(d);
  }

  function go(to) {
    dots.children[idx].classList.remove('active');
    idx = ((to % n) + n) % n;
    track.style.transform = 'translateX(-' + (idx * 100) + '%)';
    dots.children[idx].classList.add('active');
    ctr.textContent = (idx + 1) + ' / ' + n;
  }

  document.getElementById('ssPrev').addEventListener('click', function () { go(idx - 1); });
  document.getElementById('ssNext').addEventListener('click', function () { go(idx + 1); });

  document.addEventListener('keydown', function (e) {
    if (e.key === 'ArrowRight') go(idx + 1);
    if (e.key === 'ArrowLeft')  go(idx - 1);
  });
})();
</script>
