# spoolman-monitoring — Installation

## Requirements

Spoolman native /metrics endpoint, Prometheus and Grafana.

## Procedure

Enable the Spoolman metrics endpoint, adapt examples/prometheus-scrape.yml and import dashboards/spoolman-filament.json. Select the spoolman job and instance.

The files under [examples](../examples) are reference configuration. Replace example addresses, token paths and bind addresses for your deployment.

Next, review [configuration](./configuration.md) and [dashboard usage](./usage.md).
