####  `Values`
All the listed values are related to the alerts.

##### Note:
1. The thresholds which has default values as `-1`, the alerts associated to that thresholds will not be created unless the thresholds are modified to a value greater than  `-1`.
2. Alerts can be disabled by modifying the threshold value of respective alert to `-1`.

| Inputs                                          | Type   | <div style="width:400px">Description</div>             | Default |
|-------------------------------------------------|--------|--------------------------------------------------------|---------|
| alerts.standard.infra.cronjob_restart_threshold | number | Alert if cronjob execution failed beyond the threshold | `0`     |
