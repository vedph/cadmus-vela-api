# Cadmus Vela API

🐋 Quick Docker image build:

    docker build . -t vedph2020/cadmus-vela-api:1.0.2 -t vedph2020/cadmus-vela-api:latest

(replace with the current version).

This API uses core components from the following Cadmus libraries:

- [general and philology](https://github.com/vedph/cadmus-shell-2)
- [epigraphy](https://github.com/vedph/cadmus-epigraphy)
- [geography](https://github.com/vedph/cadmus-geo)

## Graffiti

(a) general:

- external IDs\*: all the IDs linked to the inscription.
- metadata: general purpose metadata.
- geographic location(s)\*. This is used to pinpoint the inscription on a map. The link to a site is managed via the pin links part.
- date\*.

(b) epigraphy:

- support.
- writing.

(c) classification:

- categories\*: general thematic tags from a taxonomy.
- index keywords: multiple-language keywords which can be grouped under several sections ("indexes").

(d) comment:

- comment: generic comment.
- note: free text note. Might be useful for redactional purposes.

(e) references:

- references: short documentary references.
- bibliography.

(f) text:

- text: text or a part of it when required.
- apparatus layer: critical apparatus.
- orthography layer: can be used to annotate and categorize linguistic phenomena reflected in orthography.
- ligatures layer: can be used to annotate ligatures in text.
- comment layer: can be used to comment specific words of the text.
- chronology layer: can be used to mark specific words of the text (designating battles, priesthoods, magistrates, etc.) as related to a datation.

The original schema was just a flat spreadsheet table, where some columns are grouped under so-called header columns, filled with color and without data, whose purpose is making all the following columns belonging to the same group. Often this is used to represent boolean features in a mutually exclusive relationship. Of course, this is just a hack due to the flat nature of the spreadsheet model.

- A = ID (e.g. `CASTELLO_01-0001`): this can just be the title and eventually an EID in metadata part.
- B = image, I found it always empty. At any rate, once we have an ID, the image resources can be accessed via some transformation of it.
- C-E = area, sestriere, denominazione: toponyms part hierarchy.
- F-K = funzione originaria, funzione attuale, tipologia struttura, interno/esterno, supporto, materiale: epigraphic support part.
- L = "datati" (boolean): eventually in metadata.
- M-O = terminus post, terminus ante, cronologia: datation part.
- writing part: script features:
  - P figurativi
  - Q testo
  - R numero
  - S cornice
- T tipo figurativo: support part: figurative type.
- U tipo cornice: writing part: figurative features.
- V misure: support part.
- W numero righe: calculated (?).
- X alfabeto: writing part: system.
- Y lingua: writing part: languages.
- Z lingua ISO 639/3: as above.
- AA codice glottologico (?)
- AB tipologia grafica (?)
- AC tecnica esecuzione (header column): writing part: technique:
  - AD presenza di disegno
  - AE presenza di preparazione del supporto
  - AF graffio
  - AG incisione
  - AH intaglio
  - AI disegno
  - AJ punzonatura
  - AK a rilievo
- AL strumento di esecuzione (header column): writing part: tool:
  - AM chiodo
  - AN gradina
  - AO scalpello
  - AP sgorbia
  - AQ sega
  - AR bocciarda
  - AS grafite
  - AT matita di piombo
  - AU fumo di candela
  - AV inchiostro
  - AW vernice
  - AX lama (affilatura)
  - AY tipo di lama
- AZ caratteristiche grafiche (header column): writing part: script features:
  - BA maiuscolo/minuscolo
  - BB sistema interpuntivo
  - BC nessi e legamenti (note: you might also provide more details with the ligatures layer).
  - BD abbreviazioni
- BE monogrammi, lettere singole, etcc. (header column): writing part: script features:
  - BF monogrammi
  - BG lettera singola
  - BH lettere non interpretabili
  - BI disegno non interpretabile
- BJ tipologia di argomento (header column): columns BK-CG: categories part.
- CH categorie figurative (header column): writing part: columns CH-CY: figurative type and features.
- CZ (header column): edizione e commento:
  - DA edizione
  - DB codice iconclass: in figurative type/features.
  - DC commento
  - DD osservazioni sullo stato di conservazione: support part.
  - DE bibliografia: bibliography part.
  - DF data primo rilievo: metadata or add to support part, depending on how typical we can estimate this property.
  - DG data ultima ricognizione: support part.

## History

- 2023-03-14: updated facet "required" properties.

### 1.0.2

- 2023-03-11: updated packages.
- 2023-03-07: updated packages.

### 1.0.1

- 2023-02-11: updated packages.

### 1.0.0

- 2023-02-07: migrated to new components factory. This is a breaking change for backend components, please see [this page](https://myrmex.github.io/overview/cadmus/dev/history/#2023-02-01---backend-infrastructure-upgrade). Anyway, in the end you just have to update your libraries and a single namespace reference. Benefits include:
  - more streamlined component instantiation.
  - more functionality in components factory, including DI.
  - dropped third party dependencies.
  - adopted standard MS technologies for DI.

- 2023-01-17:
  - updated packages.
  - updated thesauri.
