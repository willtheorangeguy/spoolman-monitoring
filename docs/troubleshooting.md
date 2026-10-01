# spoolman-monitoring — Troubleshooting

| Symptom | Check |
|---|---|
| All panels blank | check the spoolman job and target. |
| Remaining weight blank for a spool | inspect whether both initial and used weight metrics share spool_id and filament_id. |
| Vendor or material absent | inspect spoolman_filament_info labels. |

## First checks

Check the selected Grafana data source and dashboard variables in [configuration](./configuration.md). For Prometheus, inspect the target state and the exact job and instance labels before changing panel queries.
