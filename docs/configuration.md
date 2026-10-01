# Configuration

## Precedence

This repository combines dashboard defaults with settings for external services. It defines no shared command-line, environment variable and configuration-file override order; each external service resolves its own settings.

## Integration settings

The example target is spoolman.example:7912 with /metrics. The dashboard variables prometheus_ds, job_spoolman and instance select the data. Keep /metrics on a private monitoring network because labels contain inventory information.

## Dashboard variables

| Option | Type | Default | Description |
| --- | --- | --- | --- |
| `spoolman-filament.json / prometheus_ds` | datasource | `prometheus` | Grafana data source selected by the dashboard. |
| `spoolman-filament.json / job_spoolman` | textbox | `spoolman` | Dashboard variable whose value selects a scrape job, instance or endpoint. |
| `spoolman-filament.json / instance` | query | `label_values(up{job="${job_spoolman}"}, instance)` | Queries the data source for available values. |

## Prometheus jobs

The supplied [scrape example](https://github.com/willtheorangeguy/spoolman-monitoring/blob/HEAD/examples/prometheus-scrape.yml) defines `spoolman`. Copy its entries into your own scrape_configs and replace documentation hostnames. Job names can change if the dashboard variables change with them.

## Examples

The complete scrape job examples are in [`examples/prometheus-scrape.yml`](https://github.com/willtheorangeguy/spoolman-monitoring/blob/HEAD/examples/prometheus-scrape.yml). Copy the relevant job into your Prometheus configuration and replace the example targets.
