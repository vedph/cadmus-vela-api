# Cadmus Vela API

🐋 Quick Docker image build:

    docker build . -t vedph2020/cadmus-vela-api:1.0.2 -t vedph2020/cadmus-vela-api:latest

(replace with the current version).

- [VeLA core](https://github.com/vedph/cadmus-vela)
- [VeLA app](https://github.com/vedph/cadmus-vela-app)

This API uses core components from the following Cadmus libraries:

- [general and philology](https://github.com/vedph/cadmus-shell-2)
- [epigraphy](https://github.com/vedph/cadmus-epigraphy)
- [geography](https://github.com/vedph/cadmus-geo)

## History

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
