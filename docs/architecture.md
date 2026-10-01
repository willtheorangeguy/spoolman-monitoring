# Architecture

This project connects its data source to its Grafana dashboard through the components shown below.

## Overview

This diagram shows the data path for this project.

```mermaid
graph LR
  A[Spoolman /metrics] -->|scraped by| B[Prometheus]
  B -->|queried by| C[Grafana dashboard]
```

## Components

### Data source

Spoolman /metrics -> Prometheus -> Grafana inventory dashboard.

### Dashboard

`dashboards/spoolman-filament.json` contains the Grafana dashboard definition.

## Data flow

Spoolman /metrics -> Prometheus -> Grafana inventory dashboard. Grafana evaluates dashboard queries against the selected data source and label values.

## Directory layout

```text
.
├── dashboards/  Grafana dashboard JSON files
├── examples/  Scrape and deployment examples
├── docs/        Documentation source
└── README.md    Project overview and quick links
```
