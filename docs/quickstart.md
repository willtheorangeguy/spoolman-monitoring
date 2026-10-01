# spoolman-monitoring — Quickstart

## Prerequisites

Spoolman native /metrics endpoint, Prometheus and Grafana.

## Set up

Enable the Spoolman metrics endpoint, adapt examples/prometheus-scrape.yml and import dashboards/spoolman-filament.json. Select the spoolman job and instance.

The example Prometheus scrape job names are `spoolman`.

## Confirm data

In Prometheus, check `up{job="spoolman"}` and inspect a panel query in Grafana.
For missing data, see [troubleshooting](./troubleshooting.md).
