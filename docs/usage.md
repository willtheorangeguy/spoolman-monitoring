# Dashboard usage

Import the JSON files using **Grafana → Dashboards → New → Import**. Set the data source and variables listed in [configuration](configuration.md).

## Spoolman Filament Inventory

Source: [`dashboards/spoolman-filament.json`](https://github.com/willtheorangeguy/spoolman-monitoring/blob/HEAD/dashboards/spoolman-filament.json). Refresh: `30s`.

<!-- Screenshot: after adding spoolman-filament.png to .github/icons/spoolman-monitoring/, replace this comment with ![Spoolman Filament Inventory](https://raw.githubusercontent.com/willtheorangeguy/.github/main/icons/spoolman-monitoring/spoolman-filament.png). -->

### Panels

| Panel | Type | What it shows |
| --- | --- | --- |
| Tracked Spools | stat | See the query reference below. |
| Filament Variants | stat | See the query reference below. |
| Vendors | stat | See the query reference below. |
| Remaining Filament | stat | Net remaining weight across currently tracked spools. |
| Used on Tracked Spools | stat | Current used-weight readings; this is not lifetime filament consumption. |
| Spools Below 20% | stat | Remaining percentage relative to each spool's initial net weight. |
| Inventory Weight History | timeseries | Snapshot of currently tracked spools; totals can change when spools are added or removed. |
| Remaining by Spool | bargauge | Exact remaining net weight for each spool. |
| Current Spool Inventory — Remaining Weight | table | One row per spool with its actual vendor, filament, material, color, IDs and remaining grams. |
| Remaining Percentage by Spool | bargauge | Relative to each spool's initial net weight. |
| Spools by Material | bargauge | See the query reference below. |
| Remaining Weight by Material | timeseries | See the query reference below. |
| Spools by Vendor | bargauge | See the query reference below. |

<!-- Screenshot: add a focused panel or section image here after uploading it to .github/icons/spoolman-monitoring/. -->

### Reading the results

Remaining weight is initial net weight minus current used weight; it is not lifetime consumption. Snapshot totals change when spools enter or leave inventory. Material and vendor series come from filament metadata joined by filament_id.

### Query reference

These expressions are copied from the dashboard JSON. Grafana substitutes the dashboard variables at runtime.

#### Tracked Spools

```promql
count(spoolman_spool_initial_weight{job="${job_spoolman}",instance="$instance"})
```

#### Filament Variants

```promql
count(spoolman_filament_info{job="${job_spoolman}",instance="$instance"})
```

#### Vendors

```promql
count(count by(vendor) (spoolman_filament_info{job="${job_spoolman}",instance="$instance"}))
```

#### Remaining Filament

```promql
sum((spoolman_spool_initial_weight{job="${job_spoolman}",instance="$instance"} - on(spool_id,filament_id) spoolman_spool_weight_used{job="${job_spoolman}",instance="$instance"})) / 1000
```

#### Used on Tracked Spools

```promql
sum(spoolman_spool_weight_used{job="${job_spoolman}",instance="$instance"}) / 1000
```

#### Spools Below 20%

```promql
count(((spoolman_spool_initial_weight{job="${job_spoolman}",instance="$instance"} - on(spool_id,filament_id) spoolman_spool_weight_used{job="${job_spoolman}",instance="$instance"}) / on(spool_id,filament_id) spoolman_spool_initial_weight{job="${job_spoolman}",instance="$instance"}) < 0.2) or on() (0 * count(spoolman_spool_initial_weight{job="${job_spoolman}",instance="$instance"}))
```

#### Inventory Weight History

```promql
sum((spoolman_spool_initial_weight{job="${job_spoolman}",instance="$instance"} - on(spool_id,filament_id) spoolman_spool_weight_used{job="${job_spoolman}",instance="$instance"})) / 1000
sum(spoolman_spool_weight_used{job="${job_spoolman}",instance="$instance"}) / 1000
```

#### Remaining by Spool

```promql
((spoolman_spool_initial_weight{job="${job_spoolman}",instance="$instance"} - on(spool_id,filament_id) spoolman_spool_weight_used{job="${job_spoolman}",instance="$instance"}) * on(filament_id) group_left(name,material,vendor,color) spoolman_filament_info{job="${job_spoolman}",instance="$instance"})
```

#### Current Spool Inventory — Remaining Weight

```promql
((spoolman_spool_initial_weight{job="${job_spoolman}",instance="$instance"} - on(spool_id,filament_id) spoolman_spool_weight_used{job="${job_spoolman}",instance="$instance"}) * on(filament_id) group_left(name,material,vendor,color) spoolman_filament_info{job="${job_spoolman}",instance="$instance"})
```

#### Remaining Percentage by Spool

```promql
100 * (spoolman_spool_initial_weight{job="${job_spoolman}",instance="$instance"} - on(spool_id,filament_id) spoolman_spool_weight_used{job="${job_spoolman}",instance="$instance"}) / on(spool_id,filament_id) spoolman_spool_initial_weight{job="${job_spoolman}",instance="$instance"}
```

#### Spools by Material

```promql
count by(material) (spoolman_spool_initial_weight{job="${job_spoolman}",instance="$instance"} * on(filament_id) group_left(material) spoolman_filament_info{job="${job_spoolman}",instance="$instance"})
```

#### Remaining Weight by Material

```promql
sum by(material) ((spoolman_spool_initial_weight{job="${job_spoolman}",instance="$instance"} - on(spool_id,filament_id) spoolman_spool_weight_used{job="${job_spoolman}",instance="$instance"}) * on(filament_id) group_left(material) spoolman_filament_info{job="${job_spoolman}",instance="$instance"}) / 1000
```

#### Spools by Vendor

```promql
count by(vendor) (spoolman_spool_initial_weight{job="${job_spoolman}",instance="$instance"} * on(filament_id) group_left(vendor) spoolman_filament_info{job="${job_spoolman}",instance="$instance"})
```
