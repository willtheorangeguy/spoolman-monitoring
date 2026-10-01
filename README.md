<h1 align="center">spoolman-monitoring</h1>
<h4 align="center">A Grafana dashboard for Spoolman spool weights, remaining filament, materials and vendors using native Prometheus metrics.</h4>

<div align="center">
  <img alt="GitHub Issues" src="https://img.shields.io/github/issues/willtheorangeguy/spoolman-monitoring">
  <img alt="GitHub Pull Requests" src="https://img.shields.io/github/issues-pr/willtheorangeguy/spoolman-monitoring">
  <img alt="License: MIT" src="https://img.shields.io/badge/license-MIT-blue">
  <img alt="gitleaks workflow" src="https://github.com/willtheorangeguy/spoolman-monitoring/actions/workflows/gitleaks.yml/badge.svg">
  <img alt="testing workflow" src="https://github.com/willtheorangeguy/spoolman-monitoring/actions/workflows/testing.yml/badge.svg">
</div>

<p align="center">
  <a href="#key-features">Key Features</a> •
  <a href="#installation">Installation</a> •
  <a href="#usage">Usage</a> •
  <a href="#documentation">Documentation</a> •
  <a href="#support">Support</a> •
  <a href="#contributing">Contributing</a> •
  <a href="#license">License</a>
</p>

<!-- Screenshot: after adding spoolman-monitoring/overview.png to .github/icons/, replace this comment with ![Dashboard overview](https://raw.githubusercontent.com/willtheorangeguy/.github/main/icons/spoolman-monitoring/overview.png). -->

A Grafana dashboard for Spoolman spool weights, remaining filament, materials and vendors using native Prometheus metrics.

## Key Features

- Remaining filament weight by spool and material.
- Inventory grouped by vendor and material.
- Low remaining percentage view.
- Native Spoolman metrics with no separate exporter.

## Installation

Spoolman native /metrics endpoint, Prometheus and Grafana. Enable the Spoolman metrics endpoint, adapt examples/prometheus-scrape.yml and import dashboards/spoolman-filament.json. Select the spoolman job and instance. See [installation](docs/installation.md) for more detail.

## Usage

Import [spoolman-filament.json](dashboards/spoolman-filament.json) in Grafana using **Dashboards → New → Import**. Choose the data source and match the dashboard variables to your monitoring labels. See [dashboard usage](docs/usage.md).

## Documentation

Full documentation lives in [docs/](docs/index.md): [Quickstart](docs/getting-started.md) · [Configuration](docs/configuration.md) · [Architecture](docs/architecture.md) · [Dashboard usage](docs/usage.md) · [Troubleshooting](docs/troubleshooting.md).

## Support

Open a [GitHub Discussion](https://github.com/willtheorangeguy/spoolman-monitoring/discussions/new) or file an [issue](https://github.com/willtheorangeguy/spoolman-monitoring/issues/new/choose).

## Contributing

Contributions welcome. See the org-wide [Contributing Guide](https://github.com/willtheorangeguy/.github/blob/main/CONTRIBUTING.md) and [Code of Conduct](https://github.com/willtheorangeguy/.github/blob/main/CODE_OF_CONDUCT.md).

## License

MIT — see [LICENSE.md](LICENSE.md).
