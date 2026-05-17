# 🔭 DWARF 3 Beobachtungsplaner

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

Ein vollständiger, browserbasierter Beobachtungsplaner für das **DWARF 3 Smart-Teleskop** — entwickelt für Amateurastromen, die mit minimalem Aufwand maximalen wissenschaftlichen Nutzen aus jeder Beobachtungsnacht herausholen möchten.

**→ [Live-Demo öffnen](https://karl-friedrich-krey.github.io/dwarf3-planner/)**

---

## 📸 Überblick

Der Planner läuft vollständig im Browser — **kein Server, keine Installation, keine API-Keys**. Alle astronomischen Berechnungen erfolgen lokal in JavaScript (Meeus-Ephemeris). Wetter- und Sonnendaten werden automatisch von freien APIs abgerufen.

---

## ✨ Funktionen

### Beobachtungsbedingungen
- **Echtzeit-Wetterdaten** für den gewählten Standort (Open-Meteo API): Temperatur, Bewölkung, Luftfeuchtigkeit, Taupunkt, Luftdruck, Wind, Sichtweite
- **Seeing-Bewertung** (1–5 Sterne) aus Bewölkung, Wind und Luftfeuchtigkeit
- **Gesamtqualitäts-Badge** aus Seeing und Mondphase kombiniert

### Astronomische Zeiten
- Sonnenunter- und aufgang
- Bürgerliche, nautische und **astronomische Dämmerung**
- Dunkelfenster-Dauer (astronomische Nacht)

### Mondphase
- Aktuelle Phase mit Emoji und Beleuchtungsgrad
- Mondauf- und untergang
- **Deep-Sky-Ampel**: Einfluss des Mondes auf schwache Objekte

### 🪐 Sichtbare Planeten
- Alle 7 Planeten (Merkur–Neptun) mit lokalen Positionen (Meeus, ±1°)
- Aktuelle Höhe, Himmelsrichtung, scheinbare Helligkeit
- Auf- und Untergangszeiten
- **DWARF 3 Einstellungen** je Planet (Belichtung, Gain)

### ☄️ Kometen
- Positionsberechnung aus Keplerelementen (MPC-Daten) für bekannte Kometen
- **GoTo-Koordinaten** (RA/Dec J2000) prominent angezeigt — Klick zum Kopieren
- Tägliche Eigenbewegung in Bogenminuten
- Schritt-für-Schritt Anleitung zur Eingabe in der DWARF Lab App

### 🌠 Himmelsereignisse
- **Aktive Meteorschauer** mit ZHR, Tagen bis zum Peak und aktueller Radiant-Höhe
- Vorberechnete astronomische Ereignisse für 2026 (Oppositionen, Finsternisse, Elongationen)
- Anzeige der nächsten 60 Tage

### ☀️ Sonnenbeobachtung
- **NASA SDO HMI Live-Bild** (Weißlicht-Intensitätskarte, ~15 min Verzögerung) — entspricht dem Bild durch den DWARF 3 Weißlichtfilter
- **NOAA SWPC Aktive Regionen** (AR-Tabelle mit Fleckenklasse, McIntosh-Typ, Magnetfeldklasse)
- **GOES X-Ray Flare-Klasse** (A/B/C/M/X) in Echtzeit
- **Geomag. K-Index** mit automatischer **Polarlicht-Warnung** bei Kp ≥ 4
- Solar Flux F10.7 als Indikator für den aktuellen Sonnenzyklus
- DWARF 3 Einstellungen für den Solar-Modus
- Sicherheitshinweise zur Sonnenbeobachtung

### Deep-Sky-Objekte (10 kuratierte Ziele)
- **Automatisches Ranking** nach aktueller Höhe, maximaler Höhe der Nacht, Monddistanz und Mondphase
- **Live-Höhenkurve** (Canvas) für die nächsten 10 Stunden mit aktuellem Positionspunkt
- **Wikipedia-Archivfotos** (Wikimedia Commons API) für jedes Objekt
- Entfernung, Entdecker, Objekttyp, Winkelgröße
- **DWARF 3 Einstellungen** je Objekt: Belichtungszeit, Gain, Frame-Anzahl, korrekter Filtername
- Praxistipps speziell für den DWARF 3

### 📍 Standortauswahl
- 23 Voreinstellungen: Deutschland, Österreich, Schweiz, Europa
- **GPS-Standortbestimmung** (Browser-Geolokalisierung)
- Manuelle Eingabe von Name und Koordinaten (Dezimalgrad)
- Gespeicherte Auswahl (localStorage) — bleibt beim nächsten Öffnen erhalten
- Alle Berechnungen (Dämmerung, Planeten, Wetter) werden für den gewählten Ort neu berechnet

---

## 🔭 DWARF 3 Filter — Legende

| Filter | Wellenlänge | Einsatzbereich |
|--------|-------------|----------------|
| **VIS** | 430–650 nm | Tageslicht, Landschaft |
| **Astro** | 430–690 nm | Galaxien, Sternhaufen — reduziert Lichtverschmutzung |
| **Dual-Band** | OIII / Hα / Hβ | Emissionsnebel — blockiert Stadtlicht und Mondlicht |
| *(kein Filter)* | – | Sehr helle Objekte (Kugelsternhaufen, Planeten) |

---

## 🚀 Installation & Nutzung

### Lokal
```bash
# Einfach die Datei herunterladen und im Browser öffnen:
dwarf3_planner.html → Doppelklick → öffnet sich in Chrome/Firefox/Edge
```
Keine Installation, kein Server, keine Abhängigkeiten erforderlich.

### Über GitHub Pages hosten
1. Repository forken oder klonen
2. `dwarf3_planner.html` in `index.html` umbenennen
3. **Settings → Pages → Branch: main → Save**
4. Erreichbar unter: `https://[username].github.io/[repo-name]/`

---

## 📡 Datenquellen

| Quelle | Inhalt | Update |
|--------|--------|--------|
| [Open-Meteo](https://open-meteo.com) | Wetter, Bewölkung, Wind, Luftfeuchte | Stündlich |
| [NASA SDO / HMI](https://sdo.gsfc.nasa.gov) | Sonne: Weißlicht-Intensitätskarte | ~15 min |
| [NOAA SWPC](https://www.swpc.noaa.gov) | Sonnenflecken, Flare-Klasse, K-Index, F10.7 | 1–60 min |
| [Wikipedia API](https://www.mediawiki.org/wiki/API:Main_page) | Deep-Sky Archivfotos (Wikimedia Commons) | Statisch |
| Lokale Ephemeris | Sonne, Mond, Planeten, Kometen (Meeus J2000) | Echtzeit |
| MPC / JPL | Kometenbahnen (eingebettete Elemente, Stand 2025) | Manuell |

Alle APIs sind kostenlos und erfordern keine Registrierung oder API-Keys.

---

## 🌍 Unterstützte Standorte (Voreinstellungen)

**Deutschland:** Stralsund, Hamburg, Berlin, Dresden, Hannover, Dortmund, Köln, Frankfurt a.M., Nürnberg, Stuttgart, München, Kiel

**Österreich / Schweiz:** Wien, Salzburg, Innsbruck, Zürich, Luzern

**Europa:** London, Paris, Rom, Amsterdam, Kopenhagen, Oslo

Sowie GPS-Standortbestimmung und manuelle Koordinateneingabe für jeden Ort der Welt.

---

## ⚠️ Sicherheitshinweis Sonnenbeobachtung

> **Niemals** ohne montierten und geprüften Sonnenfilter das Teleskop auf die Sonne richten oder hindurchschauen. Der DWARF 3 Weißlichtfilter muss **vor dem Objektiv** sitzen und sicher befestigt sein. Bei sichtbaren Beschädigungen sofort ersetzen.

---

## 🔧 Technische Details

- **Sprache:** Vanilla HTML/CSS/JavaScript — keine Frameworks, keine Build-Tools
- **Astronomische Berechnungen:** Meeus-Näherungsformeln (Low-Precision, ±0.5–1°)
- **Planetenpositionen:** Kepler-Gleichung mit J2000-Elementen
- **Kometenpositionen:** Parabolische / elliptische Bahnberechnung aus MPC-Elementen
- **Dämmerungszeiten:** Iterative Suche + Binäre Präzisierung (14 Iterationen)
- **Mondpositionen:** Vereinfachte VSOP-Reihen (±0.5°)
- **Auto-Aktualisierung:** Sonnendaten alle 10 Minuten

---

## 📝 Lizenz

Dieses Projekt steht unter der [MIT-Lizenz](LICENSE) — freie Nutzung, Weitergabe und Modifikation mit Quellenangabe.

---

## 👤 Autor

**Dr. Karl-Friedrich Krey**  
Greifswald

---

*Klarer Himmel und viele scharfe Aufnahmen!* 🌌
