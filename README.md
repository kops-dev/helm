# Helm Module
- Helm helps you manage Kubernetes applications. `Helm Charts` help you define, install, and upgrade even the most complex Kubernetes application. Charts are easy to create, version, share, and publish.
- The `helm` module helps you to create Deployment, Services, HPA, ServiceMonitor, Alerts, etc. 

This helm chart can be used by kubectl command to manually deploy an application to a cluster. Continuous deployment systems 
like harness can use this helm chart to deploy any service to EKS/AKS/GKE cluster.


##### Install/ Upgrade using the below command
```
helm upgrade --install {service-name} ./service/ -f values.yaml -n {namespace}
```

### Variables

###### `cliService`
- Default: **`false`**

  Whether application is a CLI service

###### `cluster_name`
- **Required**

  Name of the Kubernetes cluster

###### `concurrencyPolicy`
- Default: **`"Replace"`**

  Name of the Kubernetes cluster

###### `DB_DIALECT`
- Default: **`""`**

  DB type(ex - mysql, postgresql are valid)


###### `default_severity`
- Default: **`critical`**

  Default severity level that alerts will be tagged to

###### `heartbeatURL`
- Default: **`"/.well-known/heartbeat"`**

  Heartbeat URL

###### `hpa_cpu_limit`
- Default: **`80`**

  HPA CPU limit

###### `hpa_memory_limit`
- Default: **`80`**

  HPA Memory limit

###### `httpPort`
- Default: **`8000`**

  Port on which container runs its services

###### `image`
- **Required**

  Docker container image with tag

###### `maxCPU`
- Default: **`"500m"`**

  Maximum CPU resources

###### `maxMemory`
- Default: **`"512Mi"`**

  Maximum Memory resources

###### `maxReplicas`
- Default: **`4`**

  Maximum replicas

###### `metricsPort`
- Default: **`2121`**

  Metrics port on which container runs its services

###### `metricsScrapeInterval`
- Default: **`"30s"`**

  Time interval that metrics will be scraped

###### `minCPU`
- Default: **`"250m"`**

  Minimum CPU resources

###### `minMemory`
- Default: **`"128Mi"`**

  Minimum Memory resources

###### `minReplicas`
- Default: **`2`**

  Minimum replicas

###### `name`
- Default: **`"hello-api"`**

  Name of the service

###### `replicaCount`
- Default: **`2`**

  Number of replicas to run

###### `schedule`
- Default: **`""`**

  cron job schedule

###### `suspend`
- Default: **`false`**

  cron job suspend

####  `alerts`
Standard alerts for the resources

| Inputs                                                             | Type             | Description                                                                                                                              | Default      |
|--------------------------------------------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------|--------------|
| custom.alert_rule                                                  | string           | Metric Name exposed by /metric endpoint                                                                                                  | `""`         |
| custom.description                                                 | string           | Custom alert if user_created events goes below threshold for 5 min                                                                       | `""`         |
| custom.label_value                                                 | optional(string) | Metric Event Name, can be empty string                                                                                                   | `""`         |
| custom.name                                                        | string           | Custom alert if user_created events goes below threshold for 5 min                                                                       | `""`         |
| custom.percentile                                                  | optional(number) | Percentile is useful for histogram queries                                                                                               | `0.0`        |
| custom.query_operator                                              | optional(string) | Query Operator                                                                                                                           | `">"`        |
| custom.severity                                                    | string           | Severity level of alert                                                                                                                  | `""`         |
| custom.sum_by_label                                                | optional(string) | Metric events key, can be empty string                                                                                                   | `""`         |
| custom.threshold                                                   | string           | Threshold                                                                                                                                | `""`         |
| custom.time_window                                                 | string           | Time window for custom alerts                                                                                                            | `""`         |
| path_method.outbound_request_count.adaptive_reference_time_window  | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| path_method.outbound_request_count.adaptive_threshold              | optional(number) | Alert if the response code count in an application goes lower 15 percent in adaptive time window over adaptive reference time window     | `-1`         |
| path_method.outbound_request_count.adaptive_time_window            | optional(string) | Time window for adaptive                                                                                                                 | `"5m"`       |
| path_method.outbound_request_count.method                          | optional(string) | Custom method given by user                                                                                                              | `".*"`       |
| path_method.outbound_request_count.path                            | optional(string) | Custom path given by user                                                                                                                | `".*"`       |
| path_method.outbound_request_count.severity_level                  | optional(string) | Severity level of alert                                                                                                                  | critical     |
| path_method.outbound_response_code.absolute_threshold              | optional(number) | Alert if the response code errors in application goes beyond absolute threshold in absolute time window                                  | `-1`         |
| path_method.outbound_response_code.absolute_time_window            | optional(string) | Time window for absolute outbound response code alerts                                                                                   | `"5m"`       |
| path_method.outbound_response_code.adaptive_threshold              | optional(number) | Alert if the response code count in an application goes beyond 15 percent in adaptive time window over adaptive reference time window    | `-1`         |
| path_method.outbound_response_code.adaptive_time_window            | optional(string) | Time window for adaptive outbound response code alerts                                                                                   | `"5m"`       |
| path_method.outbound_response_code.adaptive_reference_time_window  | optional(string) | Reference Time window                                                                                                                    | `"3h"`       | 
| path_method.outbound_response_code.method                          | optional(string) | Custom method given by user                                                                                                              | `".*"`       |
| path_method.outbound_response_code.path                            | optional(string) | Custom path given by user                                                                                                                | `".*"`       |
| path_method.outbound_response_code.percentage_threshold            | optional(number) | Alert if the response code errors in application goes beyond percentage threshold percent in percentage time window                      | `-1`         |
| path_method.outbound_response_code.percentage_time_window          | optional(string) | Time window for percentage outbound response code alerts                                                                                 | `"5m"`       |
| path_method.outbound_response_code.response_code                   | string           | Response Code for different alerts                                                                                                       |
| path_method.outbound_response_code.severity_level                  | optional(string) | Severity level of alert                                                                                                                  | critical     |
| path_method.outbound_response_time.absolute_threshold              | number           | Alert if the response code errors in application goes beyond absolute threshold in absolute time window                                  | `-1`         |
| path_method.outbound_response_time.absolute_time_window            | optional(string) | Time window for absolute outbound response time alerts                                                                                   | `"5m"`       |
| path_method.outbound_response_time.absolute_percentile             | optional(number) | percentile given by the user                                                                                                             | `-1`         |
| path_method.outbound_response_time.adaptive_threshold              | optional(number) | Alert if the response code count in an application goes beyond 15 percent in adaptive time window over adaptive reference time window    | `-1`         |
| path_method.outbound_response_time.adaptive_percentile             | optional(number) | The configurable application response percentile                                                                                         | `-1`         |
| path_method.outbound_response_time.adaptive_time_window            | optional(string) | Time window for adaptive outbound response time alerts                                                                                   | `"5m"`       |
| path_method.outbound_response_time.adaptive_reference_time_window  | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| path_method.outbound_response_time.method                          | optional(string) | Custom method given by user                                                                                                              | `".*"`       |
| path_method.outbound_response_time.path                            | optional(string) | Custom path given by user                                                                                                                | `".*"`       |
| path_method.outbound_response_time.severity_level                  | optional(string) | Severity level of alert                                                                                                                  | critical     |
| path_method.request_count.adaptive_reference_time_window           | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| path_method.request_count.adaptive_threshold                       | optional(number) | Alert if the response code count in an application goes lower 15 percent in adaptive time window over adaptive reference time window     | `-1`         |
| path_method.request_count.adaptive_time_window                     | optional(string) | Time window for adaptive request count alerts                                                                                            | `"5m"`       |
| path_method.request_count.method                                   | optional(string) | Custom method given by user                                                                                                              | `".*"`       |
| path_method.request_count.path                                     | optional(string) | Custom path given by user                                                                                                                | `".*"`       |
| path_method.request_count.severity_level                           | optional(string) | Severity level of alert                                                                                                                  | critical     |
| path_method.response_code.absolute_threshold                       | optional(number) | Alert if the response code errors in application goes beyond absolute threshold in absolute time window                                  | `-1`         |
| path_method.response_code.absolute_time_window                     | optional(string) | Time window for absolute response code alerts                                                                                            | `"5m"`       |
| path_method.response_code.adaptive_threshold                       | optional(number) | Alert if the response code count in an application goes beyond 15 percent in adaptive time window over adaptive reference time window    | `-1`         |
| path_method.response_code.adaptive_time_window                     | optional(string) | Time window for adaptive response code alerts                                                                                            | `"5m"`       |
| path_method.response_code.adaptive_reference_time_window           | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| path_method.response_code.method                                   | optional(string) | Custom method given by user                                                                                                              | `".*"`       |
| path_method.response_code.path                                     | optional(string) | Custom path given by user                                                                                                                | `".*"`       |
| path_method.response_code.percentage_threshold                     | optional(number) | Alert if the response code errors in application goes beyond percentage threshold percent in percentage time window                      | `-1`         |
| path_method.response_code.percentage_time_window                   | optional(string) | Time window for percentage response code alerts                                                                                          | `"5m"`       |
| path_method.response_code.response_code                            | string           | Response Code for different alerts                                                                                                       |
| path_method.response_code.severity_level                           | optional(string) | Severity level of alert                                                                                                                  | critical     |
| path_method.response_time.absolute_threshold                       | number           | Alert if the response code errors in application goes beyond absolute threshold in absolute time window                                  | `-1`         |
| path_method.response_time.absolute_time_window                     | optional(string) | Time window for absolute response time alerts                                                                                            | `"5m"`       |
| path_method.response_time.absolute_percentile                      | optional(number) | percentile given by the user                                                                                                             | `-1`         |
| path_method.response_time.adaptive_threshold                       | optional(number) | Alert if the response code count in an application goes beyond 15 percent in adaptive time window over adaptive reference time window    | `-1`         |
| path_method.response_time.adaptive_percentile                      | optional(number) | The configurable application response percentile                                                                                         | `-1`         |
| path_method.response_time.adaptive_time_window                     | optional(string) | Time window for adaptive response time alerts                                                                                            | `"5m"`       |
| path_method.response_time.adaptive_reference_time_window           | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |     
| path_method.response_time.method                                   | optional(string) | Custom method given by user                                                                                                              | `".*"`       |
| path_method.response_time.path                                     | optional(string) | Custom path given by user                                                                                                                | `".*"`       |
| path_method.response_time.severity_level                           | optional(string) | Severity level of alert                                                                                                                  | critical     |
| standard.infra.health_check_failure_threshold                      | optional(number) | Alert if  application health-check failures goes beyond 50 in a 5-minute window                                                          | `50`         |
| standard.infra.health_check_failure_time_window                    | optional(string) | Time window for health check failure                                                                                                     | `"5m"`       |
| standard.infra.hpa_nearing_max_pod_threshold                       | optional(number) | Alert if replica count crosses the threshold percentage of max pod count                                                                 | `80`         |
| standard.infra.pod_restart_threshold                               | optional(number) | Alert if the pod restarts goes beyond threshold over a 5-minute window                                                                   | `0`          |
| standard.infra.pod_restart_time_window                             | optional(string) | Time window for pod restart                                                                                                              | `"5m"`       |
| standard.infra.service_memory_utilization_threshold                | optional(number) | Alert if service memory utilization exceeds threshold                                                                                    | `90`         |
| standard.infra.service_cpu_utilization_threshold                   | optional(number) | Alert if service cpu utilization exceeds threshold                                                                                       | `90`         |
| standard.infra.service_cpu_utilization_time_window                 | optional(string) | Time window for service cpu utilization                                                                                                  | `"5m"`       |
| standard.infra.unavailable_replicas_threshold                      | optional(number) | Alert if the available replicas is lesser than number of desired replicas                                                                | `0`          |
| standard.outbound_request_count.adaptive_threshold                 | optional(number) | Alerts based on number of outbound requests                                                                                              | `30`         |
| standard.outbound_request_count.adaptive_time_window               | optional(string) | Time window for adaptive outbound request count                                                                                          | `"5m"`       |
| standard.outbound_request_count.adaptive_reference_time_window     | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| standard.outbound_response_code.201.absolute_threshold             | optional(number) | Alert if the outbound 201 response code errors in application goes beyond 10 in a 5-minute window                                        | `-1`         |
| standard.outbound_response_code.201.absolute_time_window           | optional(string) | Time window for 201 outbound absolute alerts                                                                                             | `"5m"`       |
| standard.outbound_response_code.201.adaptive_threshold             | optional(number) | Alert if the outbound 201 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window              | `-1`         |
| standard.outbound_response_code.201.adaptive_time_window           | optional(string) | Time window for 201 outbound adaptive alerts                                                                                             | `"5m"`       |
| standard.outbound_response_code.201.adaptive_reference_time_window | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| standard.outbound_response_code.201.percentage_threshold           | optional(number) | Alert if the outbound 201 response code errors in application goes beyond 10 percent in a 5-minute window                                | `-1`         |
| standard.outbound_response_code.201.percentage_time_window         | optional(string) | Time window for 201 outbound percentage alerts                                                                                           | `"5m"`       |
| standard.outbound_response_code.400.absolute_threshold             | optional(number) | Alert if the outbound 400 response code errors in application goes beyond 40 in a 5-minute window                                        | `500`        |
| standard.outbound_response_code.400.absolute_time_window           | optional(string) | Time window for 400 outbound absolute alerts                                                                                             | `"5m"`       |
| standard.outbound_response_code.400.adaptive_threshold             | optional(number) | Alert if the outbound 400 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window              | `15`         |
| standard.outbound_response_code.400.adaptive_time_window           | optional(string) | Time window for 400 outbound adaptive alerts                                                                                             | `"5m"`       |
| standard.outbound_response_code.400.adaptive_reference_time_window | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| standard.outbound_response_code.400.percentage_threshold           | optional(number) | Alert if the outbound 400 response code errors in application goes beyond 40 percent in a given time window                              | `70`         |
| standard.outbound_response_code.400.percentage_time_window         | optional(string) | Time window for 400 outbound percentage alerts                                                                                           | `"5m"`       |
| standard.outbound_response_code.401.absolute_threshold             | optional(number) | Alert if the outbound 401 response code errors in application goes beyond 40 in a 5-minute window                                        | `100`        |
| standard.outbound_response_code.401.absolute_time_window           | optional(string) | Time window for 401 outbound absolute alerts                                                                                             | `"5m"`       |
| standard.outbound_response_code.401.adaptive_threshold             | optional(number) | Alert if the outbound 401 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window              | `15`         |
| standard.outbound_response_code.401.adaptive_time_window           | optional(string) | Time window for 401 outbound adaptive alerts                                                                                             | `"5m"`       |
| standard.outbound_response_code.401.adaptive_reference_time_window | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| standard.outbound_response_code.401.percentage_threshold           | optional(number) | Alert if the outbound 401 response code errors in application goes beyond 40 percent in a given time window                              | `20`         |
| standard.outbound_response_code.401.percentage_time_window         | optional(string) | Time window for 401 outbound percentage alerts                                                                                           | `"5m"`       |
| standard.outbound_response_code.403.absolute_threshold             | optional(number) | Alert if the outbound 403 response code errors in application goes beyond 40 in a 5-minute window                                        | `100`        |
| standard.outbound_response_code.403.absolute_time_window           | optional(string) | Time window for 403 outbound absolute alerts                                                                                             | `"5m"`       |
| standard.outbound_response_code.403.adaptive_threshold             | optional(number) | Alert if the outbound 403 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window              | `15`         |
| standard.outbound_response_code.403.adaptive_time_window           | optional(string) | Time window for 403 outbound adaptive alerts                                                                                             | `"5m"`       |
| standard.outbound_response_code.403.adaptive_reference_time_window | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| standard.outbound_response_code.403.percentage_threshold           | optional(number) | Alert if the outbound 403 response code errors in application goes beyond 40 percent in a given time window                              | `70`         |
| standard.outbound_response_code.403.percentage_time_window         | optional(string) | Time window for 403 outbound percentage alerts                                                                                           | `"5m"`       |
| standard.outbound_response_code.404.absolute_threshold             | optional(number) | Alert if the outbound 404 response code errors in application goes beyond 40 in a 5-minute window                                        | `500`        |
| standard.outbound_response_code.404.absolute_time_window           | optional(string) | Time window for 404 outbound absolute alerts                                                                                             | `"5m"`       |
| standard.outbound_response_code.404.adaptive_threshold             | optional(number) | Alert if the outbound 404 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window              | `15`         |
| standard.outbound_response_code.404.adaptive_time_window           | optional(string) | Time window for 404 outbound adaptive alerts                                                                                             | `"5m"`       |
| standard.outbound_response_code.404.adaptive_reference_time_window | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| standard.outbound_response_code.404.percentage_threshold           | optional(number) | Alert if the outbound 404 response code errors in application goes beyond 40 percent in a given time window                              | `20`         |
| standard.outbound_response_code.404.percentage_time_window         | optional(string) | Time window for 404 outbound percentage alerts                                                                                           | `"5m"`       |
| standard.outbound_response_code.5xx.absolute_threshold             | optional(number) | Alert if the outbound 500 response code errors in application goes beyond 40 in a 5-minute window                                        | `40`         |
| standard.outbound_response_code.5xx.absolute_time_window           | optional(string) | Time window for 500 outbound absolute alerts                                                                                             | `"5m"`       |
| standard.outbound_response_code.5xx.adaptive_threshold             | optional(number) | Alert if the outbound 500 response code count in  an application goes beyond 15 percent in a 5min window over last 24-hour window        | `15`         |
| standard.outbound_response_code.5xx.adaptive_time_window           | optional(string) | Time window for 500 outbound adaptive alerts                                                                                             | `"5m"`       |
| standard.outbound_response_code.5xx.adaptive_reference_time_window | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| standard.outbound_response_code.5xx.percentage_threshold           | optional(number) | Alert if the outbound 500 response code errors in application goes beyond 40 percent in a given time window                              | `40`         |
| standard.outbound_response_code.5xx.percentage_time_window         | optional(string) | Time window for 500 outbound percentage alerts                                                                                           | `"5m"`       |
| standard.outbound_response_code.5xx.severity_level                 | optional(string) | Severity level of alert                                                                                                                  | `"critical"` |
| standard.outbound_response_time.absolute_critical_threshold        | optional(number) | Alert if 95 percentile application outbound  response time increases beyond 750ms over a 5-minute window                                 | `-1`         |
| standard.outbound_response_time.absolute_critical_time_window      | optional(string) | Time window for absolute critical outbound response time                                                                                 | `"5m"`       |
| standard.outbound_response_time.absolute_warning_threshold         | optional(number) | Alert if 95 percentile application outbound response time increases beyond 250ms over a 5-minute window                                  | `-1`         |
| standard.outbound_response_time.absolute_warning_time_window       | optional(string) | Time window for absolute warning outbound response time                                                                                  | `"5m"`       |
| standard.outbound_response_time.adaptive_percentile                | optional(number) | The configurable application outbound response percentile                                                                                | `0.99`       |
| standard.outbound_response_time.adaptive_threshold                 | optional(number) | Alert if 99 percentile application outbound response time increases beyond 15 percent in a last 5-minute window over last 24-hour window | `-1`         |
| standard.outbound_response_time.reference_time_window              | optional(string) | Time window total                                                                                                                        | `"3h"`       |
| standard.outbound_response_time.time_window                        | optional(string) | Time window for outbound response time                                                                                                   | `"5m"`       |
| standard.request_count.adaptive_threshold                          | optional(number) | Alerts based on number of requests                                                                                                       | `30`         |
| standard.request_count.adaptive_time_window                        | optional(string) | Time window for adaptive request count                                                                                                   | `"5m"`       |
| standard.request_count.adaptive_reference_time_window              | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| standard.response_code.201.absolute_threshold                      | optional(number) | Alert if the 201 response code errors in application goes beyond 10 in a 5-minute window                                                 | `-1`         |
| standard.response_code.201.absolute_time_window                    | optional(string) | Time window for 201 absolute alerts                                                                                                      | `"5m"`       |
| standard.response_code.201.adaptive_threshold                      | optional(number) | Alert if the 201 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window                       | `-1`         |
| standard.response_code.201.adaptive_time_window                    | optional(string) | Time window for 201 adaptive alerts                                                                                                      | `"5m"`       |
| standard.response_code.201.adaptive_reference_time_window          | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| standard.response_code.201.percentage_threshold                    | optional(number) | Alert if the 201 response code errors in application goes beyond 10 percent in a 5-minute window                                         | `-1`         |
| standard.response_code.201.percentage_time_window                  | optional(string) | Time window for 201 percentage alerts                                                                                                    | `"5m"`       |
| standard.response_code.400.absolute_threshold                      | optional(number) | Alert if the 400 response code errors in application goes beyond 40 in a 5-minute window                                                 | `500`        |
| standard.response_code.400.absolute_time_window                    | optional(string) | Time window for 400 absolute alerts                                                                                                      | `"5m"`       |
| standard.response_code.400.adaptive_threshold                      | optional(number) | Alert if the 400 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window                       | `15`         |
| standard.response_code.400.adaptive_time_window                    | optional(string) | Time window for 400 adaptive alerts                                                                                                      | `"5m"`       |
| standard.response_code.400.adaptive_reference_time_window          | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| standard.response_code.400.percentage_threshold                    | optional(number) | Alert if the 400 response code errors in application goes beyond 40 percent in a given time window                                       | `70`         |
| standard.response_code.400.percentage_time_window                  | optional(string) | Time window for 400 percentage alerts                                                                                                    | `"5m"`       |
| standard.response_code.401.absolute_threshold                      | optional(number) | Alert if the 401 response code errors in application goes beyond 40 in a 5-minute window                                                 | `100`        |
| standard.response_code.401.absolute_time_window                    | optional(string) | Time window for 401 absolute alerts                                                                                                      | `"5m"`       |
| standard.response_code.401.adaptive_threshold                      | optional(number) | Alert if the 401 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window                       | `15`         |
| standard.response_code.401.adaptive_time_window                    | optional(string) | Time window for 401 adaptive alerts                                                                                                      | `"5m"`       |
| standard.response_code.401.adaptive_reference_time_window          | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| standard.response_code.401.percentage_threshold                    | optional(number) | Alert if the 401 response code errors in application goes beyond 40 percent in a given time window                                       | `20`         |
| standard.response_code.401.percentage_time_window                  | optional(string) | Time window for 401 percentage alerts                                                                                                    | `"5m"`       |
| standard.response_code.403.absolute_threshold                      | optional(number) | Alert if the 403 response code errors in application goes beyond 40 in a 5-minute window                                                 | `100`        |
| standard.response_code.403.absolute_time_window                    | optional(string) | Time window for 403 absolute alerts                                                                                                      | `"5m"`       |
| standard.response_code.403.adaptive_threshold                      | optional(number) | Alert if the 403 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window                       | `15`         |
| standard.response_code.403.adaptive_time_window                    | optional(string) | Time window for 403 adaptive alerts                                                                                                      | `"5m"`       |
| standard.response_code.403.adaptive_reference_time_window          | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| standard.response_code.403.percentage_threshold                    | optional(number) | Alert if the 403 response code errors in application goes beyond 40 percent in a given time window                                       | `70`         |
| standard.response_code.403.percentage_time_window                  | optional(string) | Time window for 403 percentage alerts                                                                                                    | `"5m"`       |
| standard.response_code.404.absolute_threshold                      | optional(number) | Alert if the 404 response code errors in application goes beyond 40 in a 5-minute window                                                 | `500`        |
| standard.response_code.404.absolute_time_window                    | optional(string) | Time window for 404 absolute alerts                                                                                                      | `"5m"`       |
| standard.response_code.404.adaptive_threshold                      | optional(number) | Alert if the 404 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window                       | `15`         |
| standard.response_code.404.adaptive_time_window                    | optional(string) | Time window for 404 adaptive alertsTime window                                                                                           | `"5m"`       |
| standard.response_code.404.adaptive_reference_time_window          | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| standard.response_code.404.percentage_threshold                    | optional(number) | Alert if the 404 response code errors in application goes beyond 40 percent in a given time window                                       | `20`         |
| standard.response_code.404.percentage_time_window                  | optional(string) | Time window for 404 percentage alerts                                                                                                    | `"5m"`       |
| standard.response_code.409.absolute_threshold                      | optional(number) | Alert if the 409 response code errors in application goes beyond 10 in a 5-minute window                                                 | `100`        |
| standard.response_code.409absolute_time_window                     | optional(string) | Time window for 409 absolute alerts                                                                                                      | `"5m"`       |
| standard.response_code.409adaptive_threshold                       | optional(number) | Alert if the 409 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window                       | `-1`         |
| standard.response_code.409adaptive_time_window                     | optional(string) | Time window for 409 adaptive alerts                                                                                                      | `"5m"`       |
| standard.response_code.409adaptive_reference_time_window           | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| standard.response_code.409percentage_threshold                     | optional(number) | Alert if the 409 response code errors in application goes beyond 10 percent in a 5-minute window                                         | `20`         |
| standard.response_code.409percentage_time_window                   | optional(string) | Time window for 409 percentage alerts                                                                                                    | `"5m"`       |
| standard.response_code.424.absolute_threshold                      | optional(number) | Alert if the 424 response code errors in application goes beyond 10 in a 5-minute window                                                 | `10`         |
| standard.response_code.424.absolute_time_window                    | optional(string) | Time window for 424 absolute alerts                                                                                                      | `"5m"`       |
| standard.response_code.424.adaptive_threshold                      | optional(number) | Alert if the 424 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window                       | `-1`         |
| standard.response_code.424.adaptive_time_window                    | optional(string) | Time window for 424 adaptive alerts                                                                                                      | `"5m"`       |
| standard.response_code.424.adaptive_reference_time_window          | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| standard.response_code.424.percentage_threshold                    | optional(number) | Alert if the 424 response code errors in application goes beyond 10 percent in a 5-minute window                                         | `10`         |
| standard.response_code.424.percentage_time_window                  | optional(string) | Time window for 424 percentage alerts                                                                                                    | `"5m"`       |
| standard.response_code.5xx.absolute_threshold                      | optional(number) | Alert if the 500 response code errors in application goes beyond 40 in a 5-minute window                                                 | `40`         |
| standard.response_code.5xx.absolute_time_window                    | optional(string) | Time window for 500 absolute alerts                                                                                                      | `"5m"`       |
| standard.response_code.5xx.adaptive_threshold                      | optional(number) | Alert if the 500 response code count in  an application goes beyond 15 percent in a 5min window over last 24-hour window                 | `15`         |
| standard.response_code.5xx.adaptive_time_window                    | optional(string) | Time window for 500 adaptive alerts                                                                                                      | `"5m"`       |
| standard.response_code.5xx.adaptive_reference_time_window          | optional(string) | Reference Time window                                                                                                                    | `"3h"`       |
| standard.response_code.5xx.percentage_threshold                    | optional(number) | Alert if the 500 response code errors in application goes beyond 40 percent in a given time window                                       | `40`         |
| standard.response_code.5xx.percentage_time_window                  | optional(string) | Time window for 500 percentage alerts                                                                                                    | `"5m"`       |
| standard.response_code.5xx.severity_level                          | optional(string) | Severity level of alert                                                                                                                  | `"critical"` |
| standard.response_time.absolute_critical_threshold                 | optional(number) | Alert if 95 percentile application response time increases beyond 750ms over a 5-minute window                                           | `0.75`       |
| standard.response_time.absolute_critical_time_window               | optional(string) | Time window for absolute critical response time                                                                                          | `"5m"`       |
| standard.response_time.absolute_warning_threshold                  | optional(number) | Alert if 95 percentile application response time increases beyond 250ms over a 5-minute window                                           | `0.250`      |
| standard.response_time.absolute_warning_time_window                | optional(string) | Time window for absolute response time                                                                                                   | `"5m"`       |
| standard.response_time.adaptive_threshold                          | optional(number) | Alert if 99 percentile application response time increases beyond 15 percent in a last 5-minute window over last 24-hour window          | `15`         |
| standard.response_time.adaptive_percentile                         | optional(number) | The configurable application response percentile                                                                                         | `0.99`       |
| standard.response_time.adaptive_time_window                        | optional(string) | Time window for response alerts                                                                                                          | `"5m"`       |
| standard.response_time.reference_time_window                       | optional(string) | Time window total                                                                                                                        | `"3h"`       |

#### `env`
All environment variables can be passed as a map

| Inputs          | Type             | Description     | Default      |
|-----------------|------------------|-----------------|--------------|
| cloud           | optional(string) | Cloud name      | `"GCP"`      |
| HTTP_PORT       | optional(number) | HTTP port       | `8000`       |
| TRACER_URL      | optional(string) | Tracer url      | `""`         |
| TRACER_EXPORTER | optional(string) | Tracer exporter | `""`         |

#### Note: 
  The thresholds which has default values as `-1`, the alerts associated to that thresholds will not be created unless the thresholds are modified to a value greater than  `-1`.
