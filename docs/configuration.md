# spoolman-monitoring — Configuration

The example target is spoolman.example:7912 with /metrics. The dashboard variables prometheus_ds, job_spoolman and instance select the data. Keep /metrics on a private monitoring network because labels contain inventory information.

## Dashboard variables

| Dashboard | Variable | Type | Default or query |
|---|---|---|---|
| `spoolman-filament.json` | `prometheus_ds` | datasource | `prometheus` |
| `spoolman-filament.json` | `job_spoolman` | textbox | `spoolman` |
| `spoolman-filament.json` | `instance` | query | `label_values(up{job="${job_spoolman}"}, instance)` |

## Prometheus jobs

The supplied [scrape example](../examples/prometheus-scrape.yml) defines `spoolman`. Copy its entries into your own scrape_configs and replace documentation hostnames. Job names can change if the dashboard variables change with them.
