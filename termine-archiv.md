---
layout: default
title: Terminarchiv
---

<section id="termine-archiv" class="section">
  {% assign aktuelles_jahr = 'now' | date: '%Y' %}
  {% assign jahre = site.data.termine | sort: 'datum' | reverse | group_by_exp: 't', 't.datum | date: "%Y"' | sort: 'name' | reverse %}
  <h2>Terminarchiv</h2>
  <p class="section-intro">Alle Termine aus den vergangenen Jahren – zurück zu den <a href="{{ '/#termine' | relative_url }}">aktuellen Terminen {{ aktuelles_jahr }}</a>.</p>
  {% assign hat_alte = false %}
  {% for jahr in jahre %}
    {% if jahr.name < aktuelles_jahr %}
    {% assign hat_alte = true %}
    <h3 class="archiv-jahr">{{ jahr.name }}</h3>
    <div class="termine-grid">
      {% for termin in jahr.items %}
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
    {% endif %}
  {% endfor %}
  {% unless hat_alte %}
  <p class="section-intro">Es gibt noch keine archivierten Termine.</p>
  {% endunless %}
</section>
