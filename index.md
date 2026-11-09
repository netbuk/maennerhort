---
layout: default
title: Start
---

<section class="hero">
  <img src="{{ '/assets/logo.png' | relative_url }}" alt="Logo Männerhort" class="hero-logo">
  <h1>Männerhort</h1>
  <p class="tagline">Männerhort aus Altendiez – wir treffen uns unregelmäßig zum Darten, Trainieren und geselligen Beisammensein.</p>
</section>

<section id="termine" class="section">
  <h2>Termine</h2>
  <p class="section-intro">Unsere nächsten Termine</p>
  <div class="card-grid">
    {% for termin in site.data.termine %}
    <article class="card termin-card">
      <div class="termin-datum">
        <span class="termin-wochentag">{{ termin.wochentag }}</span>
        <span class="termin-datum-text">{{ termin.datum | date: "%d.%m.%Y" }}</span>
        <span class="termin-uhrzeit">{{ termin.uhrzeit }} Uhr</span>
      </div>
      <div class="termin-body">
        <h3>{{ termin.titel }}</h3>
        <p class="termin-ort">{{ termin.ort }}</p>
        <p>{{ termin.beschreibung }}</p>
      </div>
    </article>
    {% endfor %}
  </div>
</section>

<section id="news" class="section">
  <h2>Neuigkeiten</h2>
  <div class="news-list">
    {% for eintrag in site.data.news %}
    <article class="card news-card">
      <p class="news-datum">{{ eintrag.datum | date: "%d.%m.%Y" }}</p>
      <h3>{{ eintrag.titel }}</h3>
      <p>{{ eintrag.text }}</p>
    </article>
    {% endfor %}
  </div>
</section>

<section id="info" class="section">
  <h2>Informationen</h2>
  <div class="info-grid">
    <div class="card">
      <h3>Über uns</h3>
      <p>Wir sind der <strong>Männerhort</strong> - Altendiez, Hobby-<strong>Steeldarter</strong> aus <strong>Überzeugung</strong>. </p>
    </div>
    <div class="card">
      <h3>Treffpunkt</h3>
      <p>Wir treffen uns in unregelmäßigen Abständen im <strong>Männerhort</strong> in Altendiez. </p>
    </div>
    <div class="card">
      <h3>Steeldart</h3>
      <p>Wir spielen mit richtigen Darts :D – klassisch 501, Double-Out.</p>
    </div>
  </div>
</section>
