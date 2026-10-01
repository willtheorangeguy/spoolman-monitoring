# Spoolman filament inventory dashboard

Portable monitoring bundle with example configuration. Replace example addresses and token paths for your installation; no live credentials are included.

## Requirements

Spoolman's native Prometheus metrics endpoint and a Prometheus scrape job.

## Dashboards

- `dashboards/spoolman-filament.json`

Import the JSON in Grafana using **Dashboards > New > Import**. Select your data source from the dashboard variable(s) at the top. Update the Prometheus job variables to match your `scrape_configs` job names; use the Instance selector when present. The dashboard's JSON is also suitable for file provisioning after you have selected or provisioned data source UIDs.

Expected default job labels:

- `spoolman-filament.json`: spoolman

## Monitoring code

See the code and example configuration in this folder, if present. Keep API keys and metrics bearer tokens in local secret files or another secret manager; never commit them. Scrape examples use documentation addresses and must be edited for your network.

## Before publishing

Test against the application and Grafana versions you intend to support. Add a license you choose and check attribution for upstream components. No release or Grafana catalog upload has been performed.

## Spoolman setup

Enable Spoolman's native Prometheus endpoint, let Prometheus scrape it as job `spoolman`, and select the job and instance in Grafana. Keep `/metrics` on your private monitoring network; it includes inventory labels. Add your own Spoolman UI link after import if desired.

A sample `scrape_configs` fragment is in `examples/prometheus-scrape.yml`; replace the example hosts and token paths.
