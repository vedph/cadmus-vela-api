# Cadmus VeLA API

Cadmus editor for the [Venezia Libro Aperto project](https://projet.biblissima.fr/en/calls-projects/selected-projects/venezia-libro-aperto-vela).

🐋 Quick Docker image build:

    docker build . -t vedph2020/cadmus-vela-api:4.0.1 -t vedph2020/cadmus-vela-api:latest

(replace with the current version).

- [VeLA core](https://github.com/vedph/cadmus-vela)
- [VeLA app](https://github.com/vedph/cadmus-vela-app)

This API uses core components from the following Cadmus libraries:

- [general and philology](https://github.com/vedph/cadmus-shell-2)
- [epigraphy](https://github.com/vedph/cadmus-epigraphy)
- [geography](https://github.com/vedph/cadmus-geo)

## History

- 2024-12-20: updated packages.
- 2024-12-11: added thesauri entries.
- 2024-12-10: updated packages.
- 2024-12-03: updated packages.
- 2024-11-30: updated packages.
- 2024-11-29: updated packages.
- 2024-11-20:
  - changes in profile.
  - updated packages.

### 4.0.1

- 2024-11-19: changed seed delay name in app settings.

### 4.0.0

- 2024-11-19: ⚠️ upgraded to .NET 9.
- 2024-11-10: fix to profile.
- 2024-11-02: ⚠️ refactoring for new models.
- 2024-10-29:
  - updated packages.
- 2024-10-21: added flag for IMAI.

### 3.0.3

- 2024-10-21:
  - adjustments in profile for new form model.
  - updated packages.
- 2024-10-10: updated packages.
- 2024-09-17: updated packages.
- 2024-07-19: updated packages.

### 3.0.2

- 2024-05-19: updated packages.
- 2024-05-15: updated packages.
- 2024-04-15: added flags.
- 2024-04-14: updated packages.
- 2024-03-23: updated packages.
- 2024-02-11: updated packages.
- 2024-01-28: thesauri.
- 2024-01-26: updated packages and thesauri for minor changes in models.
- 2024-01-25: more flags.
- 2024-01-19: updated packages.
- 2024-01-04:
  - updated packages.
  - more granular logging.
- 2023-11-29: expose port 8080 in Dockerfile. This seems the default port for the API in 8.0.

### 3.0.0

- 2023-11-27: ⚠️ Upgraded to .NET 8.

### 2.0.0

- 2023-06-28: [moved to PostgreSQL database](https://myrmex.github.io/overview/cadmus/dev/history/b-rdbms/).

### 1.0.3

- 2023-03-24: added thesauri and parts.
- 2023-03-23: fixes to configuration.
- 2023-03-21: refactored data models introducing graffiti-specific parts.
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
