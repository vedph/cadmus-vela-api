# Cadmus Vela API

Quick Docker image build:

    docker build . -t vedph2020/cadmus-vela-api:1.0.1 -t vedph2020/cadmus-vela-api:latest

(replace with the current version).

This API uses core components from the following Cadmus libraries:

- [general and philology](https://github.com/vedph/cadmus-shell-2)
- [epigraphy](https://github.com/vedph/cadmus-epigraphy)
- [geography](https://github.com/vedph/cadmus-geo)

## Graffiti

a) general:

- external IDs\*: all the IDs linked to the inscription.
- metadata: general purpose metadata.
- geographic location(s)\*. This is used to pinpoint the inscription on a map. The link to a site is managed via the pin links part.
- date\*.

b) epigraphy:

- support.
- writing.

c) classification:

- categories\*: general thematic tags from a taxonomy.
- index keywords: multiple-language keywords which can be grouped under several sections ("indexes").

d) comment:

- comment: generic comment.
- note: free text note. Might be useful for redactional purposes.

e) references:

- references: short documentary references.
- bibliography.

f) text:

- text: text or a part of it when required.
- apparatus layer: critical apparatus.
- orthography layer: can be used to annotate and categorize linguistic phenomena reflected in orthography.
- ligatures layer: can be used to annotate ligatures in text.
- comment layer: can be used to comment specific words of the text.
- chronology layer: can be used to mark specific words of the text (designating battles, priesthoods, magistrates, etc.) as related to a datation.

## History

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
