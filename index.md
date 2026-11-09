---
layout: default
title: Start
---

<section class="hero">
  <img src="{{ '/assets/logo.png' | relative_url }}" alt="Logo Männerhort" class="hero-logo">
  <h1>Männerhort</h1>
  <p class="tagline">Hobby-Darter aus Altendiez – wir treffen uns unregelmäßig zum Darten, Trainieren und geselligen Beisammensein.</p>
</section>

<section id="termine" class="section">
  {% assign aktuelles_jahr = 'now' | date: '%Y' %}
  {% assign jahre = site.data.termine | sort: 'datum' | reverse | group_by_exp: 't', 't.datum | date: "%Y"' %}
  {% assign termine_aktuell = '' | split: '' %}
  {% for jahr in jahre %}
    {% if jahr.name == aktuelles_jahr %}{% assign termine_aktuell = jahr.items %}{% endif %}
  {% endfor %}
  <h2>Termine {{ aktuelles_jahr }}</h2>
  <p class="section-intro">Was ist dieses Jahr gelaufen und was steht noch an.</p>
  {% if termine_aktuell.size > 0 %}
  <div class="termine-grid">
    {% for termin in termine_aktuell %}
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
  {% else %}
  <p class="section-intro">Aktuell sind keine Termine für {{ aktuelles_jahr }} eingetragen.</p>
  {% endif %}
  <p style="margin-top: 1.25rem;"><a href="{{ '/termine-archiv/' | relative_url }}">Ältere Termine im Terminarchiv ansehen →</a></p>
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

<section id="mitglieder" class="section">
  <h2>Darter</h2>
  <p class="section-intro">The men of steel ;)</p>
  <p class="profile-legend">
    <span class="legend-item"><span class="profile-icon icon-scolia">S</span> Scolia</span>
    <span class="legend-item"><span class="profile-icon icon-autodarts">A</span> Autodarts</span>
    <span class="legend-item"><span class="profile-icon icon-grand-darts">GD</span> Grand Darts</span>
    <span class="legend-item"><span class="profile-icon icon-target">T</span> Target</span>
  </p>
  <div class="info-grid">
    {% assign mitglieder = site.data.mitglieder | sort: 'name' %}
    {% for mitglied in mitglieder %}
    <div class="card member-card">
      <h3>{{ mitglied.name }}{% if mitglied.nickname != "" %} <span class="member-nickname">aka {{ mitglied.nickname }}</span>{% endif %}</h3>
      {% if mitglied.rolle != "" %}<p class="member-meta">{{ mitglied.rolle }}</p>{% endif %}
      {% if mitglied.dabei_seit != "" %}<p class="member-meta">Dabei seit: {{ mitglied.dabei_seit }}</p>{% endif %}
      <div class="profile-list">
        {% if mitglied.profile.scolia != "" %}<div class="profile-row"><span class="profile-icon icon-scolia">S</span>{% if mitglied.profile.scolia contains "http" %}<a href="{{ mitglied.profile.scolia }}" target="_blank" rel="noopener">{{ mitglied.profile.scolia }}</a>{% else %}<span class="profile-name">{{ mitglied.profile.scolia }}</span>{% endif %}</div>{% endif %}
        {% if mitglied.profile.autodarts != "" %}<div class="profile-row"><span class="profile-icon icon-autodarts">A</span>{% if mitglied.profile.autodarts contains "http" %}<a href="{{ mitglied.profile.autodarts }}" target="_blank" rel="noopener">{{ mitglied.profile.autodarts }}</a>{% else %}<span class="profile-name">{{ mitglied.profile.autodarts }}</span>{% endif %}</div>{% endif %}
        {% if mitglied.profile.grand_darts != "" %}<div class="profile-row"><span class="profile-icon icon-grand-darts">GD</span>{% if mitglied.profile.grand_darts contains "http" %}<a href="{{ mitglied.profile.grand_darts }}" target="_blank" rel="noopener">{{ mitglied.profile.grand_darts }}</a>{% else %}<span class="profile-name">{{ mitglied.profile.grand_darts }}</span>{% endif %}</div>{% endif %}
        {% if mitglied.profile.target != "" %}<div class="profile-row"><span class="profile-icon icon-target">T</span>{% if mitglied.profile.target contains "http" %}<a href="{{ mitglied.profile.target }}" target="_blank" rel="noopener">{{ mitglied.profile.target }}</a>{% else %}<span class="profile-name">{{ mitglied.profile.target }}</span>{% endif %}</div>{% endif %}
      </div>
      {% if mitglied.wanderpokal > 0 %}
      <p class="member-trophy">🏆 Wanderpokal des Männerhort: {{ mitglied.wanderpokal }}× gewonnen</p>
      {% endif %}
    </div>
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
