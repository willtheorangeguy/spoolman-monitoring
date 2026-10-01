# spoolman-monitoring — Architecture

Spoolman native /metrics -> Prometheus -> Grafana inventory dashboard.

## Components

- [dashboards/](../dashboards): Grafana dashboard definitions
- [examples/](../examples): deployment and scrape examples

## Data interpretation

Remaining weight is initial net weight minus current used weight; it is not lifetime consumption. Snapshot totals change when spools enter or leave inventory. Material and vendor series come from filament metadata joined by filament_id.
