####  `Values`
All the listed values are related to the alerts.

##### Note:
  1. The thresholds which has default values as `-1`, the alerts associated to that thresholds will not be created unless the thresholds are modified to a value greater than  `-1`.
  2. Alerts can be disabled by modifying the threshold value of respective alert to `-1`.


| Inputs                                                                    | Type             | <div style="width:400px">Description</div>                                                                                                | Default      |
|---------------------------------------------------------------------------|------------------|-------------------------------------------------------------------------------------------------------------------------------------------|--------------|
| alerts.custom                                                             | list             | For creating the custom alerts you can refer the below table values. It takes the list of values as inputs                                | `[]`         |
| alerts.standard.infra.healthCheckFailureThreshold                      | optional(number) | Alert if  application health-check failures goes beyond 50 in a 5-minute window                                                           | `50`         |
| alerts.standard.infra.healthCheckFailureTimeWindow                    | optional(string) | Time window for health check failure                                                                                                      | `"5m"`       |
| alerts.standard.infra.hpaNearingMaxPodThreshold                       | optional(number) | Alert if replica count crosses the threshold percentage of max pod count                                                                  | `80`         |
| alerts.standard.infra.podRestartThreshold                               | optional(number) | Alert if the pod restarts goes beyond threshold over a 5-minute window                                                                    | `0`          |
| alerts.standard.infra.podRestartTimeWindow                             | optional(string) | Time window for pod restart                                                                                                               | `"5m"`       |
| alerts.standard.infra.serviceMemoryUtilizationThreshold                | optional(number) | Alert if service memory utilization exceeds threshold                                                                                     | `90`         |
| alerts.standard.infra.serviceCpuUtilizationThreshold                   | optional(number) | Alert if service cpu utilization exceeds threshold                                                                                        | `90`         |
| alerts.standard.infra.serviceCpuUtilizationTimeWindow                 | optional(string) | Time window for service cpu utilization                                                                                                   | `"5m"`       |
| alerts.standard.infra.unavailableReplicasThreshold                      | optional(number) | Alert if the available replicas is lesser than number of desired replicas                                                                 | `0`          |

#### `custom-alerts`

| Inputs          | Type             | Description                                                                                     | Default |
|-----------------|------------------|-------------------------------------------------------------------------------------------------|---------|
| alertRule      | optional(string) | Metric Name exposed by /metric endpoint (eg. "user_post_get_counter")                           | nil     |
| description     | optional(string) | Description of custom alert (eg. "alert if user_created events goes below threshold for 5 min") | `""`    |
| labelValue     | optional(string) | Metric Event Name (eg. "user_created")                                                          | `""`    |
| labels.severity | optional(string) | Severity for the alert (eg. "critical" or "warning")                                            | `""`    |
| name            | string           | Name of the alert (eg. "custom alert if user_created events goes below threshold for 5 min")    | `""`    |
| percentile      | optional(number) | Percentile is useful for histogram queries (eg. 0.99 percentile)                                | `0.0`   |
| queryOperator  | optional(string) | Query Operator to compare the thresholds values                                                 | `>`     |
| sumByLabel    | optional(string) | Metric events key (eg. "events")                                                                | `""`    |
| timeWindow     | optional(string) | Time window for the custom alerts                                                               | `""`    |
| threshold       | optional(number) | Threshold value for custom alerts                                                               | `""`    |

