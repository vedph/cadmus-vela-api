# Cadmus Vela API

🐋 Quick Docker image build:

    docker build . -t vedph2020/cadmus-vela-api:1.0.2 -t vedph2020/cadmus-vela-api:latest

(replace with the current version).

This API uses core components from the following Cadmus libraries:

- [general and philology](https://github.com/vedph/cadmus-shell-2)
- [epigraphy](https://github.com/vedph/cadmus-epigraphy)
- [geography](https://github.com/vedph/cadmus-geo)

## Data Model

Currently the data model includes only the item type representing a single graffiti (see the [Cadmus models shop](https://cadmus.fusi-soft.com/#/models/shop)).

### Graffiti

(a) general:

- external IDs\* (`it.vedph.external-ids`): all the IDs linked to the inscription.
- metadata (`it.vedph.metadata`): general purpose metadata.
- geographic location(s)\* (`it.vedph.geo.asserted-locations`). This is used to pinpoint the inscription on a map. The link to a site is managed via the pin links part.
- toponym(s) (`it.vedph.geo.asserted-toponyms`).
- date\* (`it.vedph.historical-date`).

(b) epigraphy:

- support (`it.vedph.epigraphy.support`).
- writing (`it.vedph.epigraphy.writing`).

(c) classification:

- categories\* (`it.vedph.categories`): general thematic tags from a taxonomy.
- index keywords (`it.vedph.index-keywords`): multiple-language keywords which can be grouped under several sections ("indexes").

(d) comment:

- comment (`it.vedph.comment`): generic comment.
- note (`it.vedph.note`): free text note. Might be useful for redactional purposes.

(e) references:

- references (`it.vedph.doc-references`): short documentary references.
- bibliography (`it.vedph.bibliography`).

(f) text:

- text (`it.vedph.token-text`): text or a part of it when required.
- apparatus layer (`it.vedph.token-text-layer` with role `fr.it.vedph.apparatus`): critical apparatus.
- ligatures layer (`it.vedph.token-text-layer` with role `fr.it.vedph.epigraphy.ligatures`): can be used to annotate ligatures in text.
- comment layer (`it.vedph.token-text-layer` with role `fr.it.vedph.comment`): can be used to comment specific words of the text.
- orthography layer (`it.vedph.token-text-layer` with role `fr.it.vedph.orthography`): can be used to annotate and categorize linguistic phenomena reflected in orthography.
- chronology layer (`it.vedph.token-text-layer` with role `fr.it.vedph.chronology`): can be used to mark specific words of the text (designating battles, priesthoods, magistrates, etc.) as related to a datation.

The original schema was just a flat spreadsheet table, where some columns are grouped under so-called header columns, filled with color and without data, whose purpose is making all the following columns belonging to the same group. Often this is used to represent boolean features in a mutually exclusive relationship. Of course, this is just a hack due to the flat nature of the spreadsheet model.

- A = ID (e.g. `CASTELLO_01-0001`): this can just be the item's **title** and eventually an EID in **metadata part**.
- B = image, I found it always empty. At any rate, once we have an ID, the image resources can be accessed via some transformation of it.
- C-E = area, sestriere, denominazione: **toponyms part** hierarchy. 📚
- F-K = funzione originaria, funzione attuale, tipologia struttura, interno/esterno, supporto, materiale: **epigraphic support part** (📚 `epi-support-materials`, `epi-support-functions`, `epi-support-object-types`, `epi-support-types`).
- L = "datati" (boolean): eventually in **metadata part**.
- M-O = terminus post, terminus ante, cronologia: **datation part**.
- **writing part**: script features (📚 `epi-writing-script-features`):
  - P figurativi
  - Q testo
  - R numero
  - S cornice
- T tipo figurativo: **support part**: figurative type (📚 `epi-writing-fig-types`).
- U tipo cornice: **writing part**: figurative features (📚 `epi-writing-fig-features`).
- V misure: **support part**: size.
- W numero righe: **writing part**: counts (📚 `decorated-count-ids`, `decorated-count-tags`).
- X alfabeto: **writing part**: system.
- Y lingua: **writing part**: languages.
- Z lingua ISO 639/3: as above.
- AA codice glottologico (?)
- AB tipologia grafica (?)
- AC tecnica esecuzione (header column): **writing part**: technique (📚 `epi-writing-techniques`):
  - AD presenza di disegno
  - AE presenza di preparazione del supporto
  - AF graffio
  - AG incisione
  - AH intaglio
  - AI disegno
  - AJ punzonatura
  - AK a rilievo
- AL strumento di esecuzione (header column): **writing part**: tool (📚 `epi-writing-tools`):
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
- AZ caratteristiche grafiche (header column): **writing part**: script features (📚 `epi-writing-script-features`):
  - BA maiuscolo/minuscolo
  - BB sistema interpuntivo
  - BC nessi e legamenti (note: you might also provide more details with the **ligatures layer** with 📚 `epi-ligature-types`).
  - BD abbreviazioni
- BE monogrammi, lettere singole, etcc. (header column): **writing part**: script features (📚 `epi-writing-script-features`):
  - BF monogrammi
  - BG lettera singola
  - BH lettere non interpretabili
  - BI disegno non interpretabile
- BJ tipologia di argomento (header column): columns BK-CG: **categories part** (📚 `categories`).
- CH categorie figurative (header column): **writing part**: columns CH-CY: figurative type and features (📚 `epi-writing-fig-types`, `epi-writing-fig-features`).
- CZ (header column): edizione e commento:
  - DA edizione: **bibliography part** (📚 `bibliography-author-roles`, `bibliography-languages`, `bibliography-types`).
  - DB codice iconclass: in **writing part**: figurative type/features (in IDs).
  - DC commento: **comment part**.
  - DD osservazioni sullo stato di conservazione: **support part**.
  - DE bibliografia: **bibliography part**.
  - DF data primo rilievo: **metadata part**, or add to support part, depending on how typical we can estimate this property.
  - DG data ultima ricognizione: **support part**.

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
