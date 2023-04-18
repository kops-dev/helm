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

###### `name`
- Default: **`"hello-api"`**

  Name of the service

###### `replicaCount`
- Default: **`2`**

  Number of replicas to run

###### `image`
- **Required**

  Docker container image with tag

###### `httpPort`
- Default: **`8000`**

  Port on which container runs its services

###### `metricsPort`
- Default: **`2121`**

  Metrics port on which container runs its services

###### `metricsScrapeInterval`
- Default: **`"30s"`**

  Time interval that metrics will be scraped

###### `cliService`
- Default: **`false`**

  Whether application is a CLI service

###### `heartbeatURL`
- Default: **`"/.well-known/heartbeat"`**

  Heartbeat URL

###### `cluster_name`
- **Required**

  Name of the Kubernetes cluster

###### `DB_DIALECT`
- Default: **`""`**

  DB type(ex - mysql, postgresql are valid)
  
###### `default_severity`
- Default: **`critical`**

  Default severity level that alerts will be tagged to

#### `Resource allocation`

| Inputs                           | Type             | Description                | Default   |
|----------------------------------|------------------|----------------------------|-----------|
| minCPU                           | optional(string) | Minimum CPU                | `"250m"`  |
| minMemory                        | optional(string) | Minimum memory             | `"128Mi"` |
| maxCPU                           | optional(string) | Maximum CPU                | `"500m"`  |
| maxMemory                        | optional(string) | Maximum memory             | `"512Mi"` |
| minReplicas                      | optional(number) | Minimum number of replicas | `2`       |
| maxReplicas                      | optional(number) | Maximum number of replicas | `4`       |
| hpa_cpu_limit                    | optional(number) | HPA CPU limit              | `80`      |
| hpa_memory_limit                 | optional(number) | HPA memory limit           | `80`      |

#### `cron JOB`

| Inputs            | Type             | Description        | Default      |
|-------------------|------------------|--------------------|--------------|
| schedule          | optional(string) | schedule           | `""`         |
| suspend           | optional(bool)   | suspend            | `false`      |
| concurrencyPolicy | optional(string) | Concurrency policy | `"Replace"`  |

#### `env`
All environment variables can be passed as a map

| Inputs          | Type             | Description     | Default      |
|-----------------|------------------|-----------------|--------------|
| cloud           | optional(string) | Cloud name      | `"GCP"`      |
| HTTP_PORT       | optional(number) | HTTP port       | `8000`       |
| TRACER_URL      | optional(string) | Tracer url      | `""`         |
| TRACER_EXPORTER | optional(string) | Tracer exporter | `""`         |


#### `alerts_standard_infra`
Standard alerts for Infra resources

| Inputs                               | Type             | Description                                                                     | Default |
|--------------------------------------|------------------|---------------------------------------------------------------------------------|---------|
| unavailable_replicas_threshold       | optional(number) | Alert if the available replicas is lesser than number of desired replicas       | `0`     |
| pod_restart_threshold                | optional(number) | Alert if the pod restarts goes beyond threshold over a 5-minute window          | `0`     |
| pod_restart_time_window              | optional(string) | Time window for pod restart                                                     | `"5m"`  |
| hpa_nearing_max_pod_threshold        | optional(number) | Alert if replica count crosses the threshold percentage of max pod count        | `80`    |
| service_memory_utilization_threshold | optional(number) | Alert if service memory utilization exceeds threshold                           | `90`    |
| service_cpu_utilization_threshold    | optional(number) | Alert if service cpu utilization exceeds threshold                              | `90`    |
| service_cpu_utilization_time_window  | optional(string) | Time window for service cpu utilization                                         | `"5m"`  |
| health_check_failure_threshold       | optional(number) | Alert if  application health-check failures goes beyond 50 in a 5-minute window | `50`    |
| health_check_failure_time_window     | optional(string) | Time window for health check failure                                            | `"5m"`  |


#### `alerts_standard_response_code`
 
- ###### `400`

| Inputs                         | Type             | Description                                                                                                        | Default |
|--------------------------------|------------------|--------------------------------------------------------------------------------------------------------------------|---------|
| absolute_threshold             | optional(number) | Alert if the 400 response code errors in application goes beyond 40 in a 5-minute window                           | `500`   |
| absolute_time_window           | optional(string) | Time window for 400 absolute alerts                                                                                | `"5m"`  |
| percentage_threshold           | optional(number) | Alert if the 400 response code errors in application goes beyond 40 percent in a given time window                 | `70`    |
| percentage_time_window         | optional(string) | Time window for 400 percentage alerts                                                                              | `"5m"`  |
| adaptive_threshold             | optional(number) | Alert if the 400 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window | `15`    |
| adaptive_time_window           | optional(string) | Time window for 400 adaptive alerts                                                                                | `"5m"`  |
| adaptive_reference_time_window | optional(string) | Reference Time window                                                                                              | `"3h"`  |

- ###### `401`

| Inputs                         | Type             | Description                                                                                                        | Default |
|--------------------------------|------------------|--------------------------------------------------------------------------------------------------------------------|---------|
| absolute_threshold             | optional(number) | Alert if the 401 response code errors in application goes beyond 40 in a 5-minute window                           | `100`   |
| absolute_time_window           | optional(string) | Time window for 401 absolute alerts                                                                                | `"5m"`  |
| percentage_threshold           | optional(number) | Alert if the 401 response code errors in application goes beyond 40 percent in a given time window                 | `20`    |
| percentage_time_window         | optional(string) | Time window for 401 percentage alerts                                                                              | `"5m"`  |
| adaptive_threshold             | optional(number) | Alert if the 401 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window | `15`    |
| adaptive_time_window           | optional(string) | Time window for 401 adaptive alerts                                                                                | `"5m"`  |
| adaptive_reference_time_window | optional(string) | Reference Time window                                                                                              | `"3h"`  |


- ###### `403`

| Inputs                         | Type             | Description                                                                                                        | Default |
|--------------------------------|------------------|--------------------------------------------------------------------------------------------------------------------|---------|
| absolute_threshold             | optional(number) | Alert if the 403 response code errors in application goes beyond 40 in a 5-minute window                           | `100`   |
| absolute_time_window           | optional(string) | Time window for 403 absolute alerts                                                                                | `"5m"`  |
| percentage_threshold           | optional(number) | Alert if the 403 response code errors in application goes beyond 40 percent in a given time window                 | `70`    |
| percentage_time_window         | optional(string) | Time window for 403 percentage alerts                                                                              | `"5m"`  |
| adaptive_threshold             | optional(number) | Alert if the 403 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window | `15`    |
| adaptive_time_window           | optional(string) | Time window for 403 adaptive alerts                                                                                | `"5m"`  |
| adaptive_reference_time_window | optional(string) | Reference Time window                                                                                              | `"3h"`  |


- ###### `404`

| Inputs                         | Type             | Description                                                                                                        | Default |
|--------------------------------|------------------|--------------------------------------------------------------------------------------------------------------------|---------|
| absolute_threshold             | optional(number) | Alert if the 404 response code errors in application goes beyond 40 in a 5-minute window                           | `500`   |
| absolute_time_window           | optional(string) | Time window for 404 absolute alerts                                                                                | `"5m"`  |
| percentage_threshold           | optional(number) | Alert if the 404 response code errors in application goes beyond 40 percent in a given time window                 | `20`    |
| percentage_time_window         | optional(string) | Time window for 404 percentage alerts                                                                              | `"5m"`  |
| adaptive_threshold             | optional(number) | Alert if the 404 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window | `15`    |
| adaptive_time_window           | optional(string) | Time window for 404 adaptive alertsTime window                                                                     | `"5m"`  |
| adaptive_reference_time_window | optional(string) | Reference Time window                                                                                              | `"3h"`  |

- ###### `5xx`

| Inputs                         | Type             | Description                                                                                                              | Default      |
|--------------------------------|------------------|--------------------------------------------------------------------------------------------------------------------------|--------------|
| absolute_threshold             | optional(number) | Alert if the 500 response code errors in application goes beyond 40 in a 5-minute window                                 | `40`         |
| absolute_time_window           | optional(string) | Time window for 500 absolute alerts                                                                                      | `"5m"`       |
| percentage_threshold           | optional(number) | Alert if the 500 response code errors in application goes beyond 40 percent in a given time window                       | `40`         |
| percentage_time_window         | optional(string) | Time window for 500 percentage alerts                                                                                    | `"5m"`       |
| adaptive_threshold             | optional(number) | Alert if the 500 response code count in  an application goes beyond 15 percent in a 5min window over last 24-hour window | `15`         |
| adaptive_time_window           | optional(string) | Time window for 500 adaptive alerts                                                                                      | `"5m"`       |
| adaptive_reference_time_window | optional(string) | Reference Time window                                                                                                    | `"3h"`       |
| severity_level                 | optional(string) | Severity level of alert                                                                                                  | `"critical"` |

- ###### `424`

| Inputs                         | Type             | Description                                                                                                        | Default |
|--------------------------------|------------------|--------------------------------------------------------------------------------------------------------------------|---------|
| absolute_threshold             | optional(number) | Alert if the 424 response code errors in application goes beyond 10 in a 5-minute window                           | `10`    |
| absolute_time_window           | optional(string) | Time window for 424 absolute alerts                                                                                | `"5m"`  |
| percentage_threshold           | optional(number) | Alert if the 424 response code errors in application goes beyond 10 percent in a 5-minute window                   | `10`    |
| percentage_time_window         | optional(string) | Time window for 424 percentage alerts                                                                              | `"5m"`  |
| adaptive_threshold             | optional(number) | Alert if the 424 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window | `-1`    |
| adaptive_time_window           | optional(string) | Time window for 424 adaptive alerts                                                                                | `"5m"`  |
| adaptive_reference_time_window | optional(string) | Reference Time window                                                                                              | `"3h"`  |


- ###### `409`

| Inputs                         | Type             | Description                                                                                                        | Default |
|--------------------------------|------------------|--------------------------------------------------------------------------------------------------------------------|---------|
| absolute_threshold             | optional(number) | Alert if the 409 response code errors in application goes beyond 10 in a 5-minute window                           | `100`   |
| absolute_time_window           | optional(string) | Time window for 409 absolute alerts                                                                                | `"5m"`  |
| percentage_threshold           | optional(number) | Alert if the 409 response code errors in application goes beyond 10 percent in a 5-minute window                   | `20`    |
| percentage_time_window         | optional(string) | Time window for 409 percentage alerts                                                                              | `"5m"`  |
| adaptive_threshold             | optional(number) | Alert if the 409 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window | `-1`    |
| adaptive_time_window           | optional(string) | Time window for 409 adaptive alerts                                                                                | `"5m"`  |
| adaptive_reference_time_window | optional(string) | Reference Time window                                                                                              | `"3h"`  |

- ###### `201`

| Inputs                         | Type             | Description                                                                                                        | Default |
|--------------------------------|------------------|--------------------------------------------------------------------------------------------------------------------|---------|
| absolute_threshold             | optional(number) | Alert if the 201 response code errors in application goes beyond 10 in a 5-minute window                           | `-1`    |
| absolute_time_window           | optional(string) | Time window for 201 absolute alerts                                                                                | `"5m"`  |
| percentage_threshold           | optional(number) | Alert if the 201 response code errors in application goes beyond 10 percent in a 5-minute window                   | `-1`    |
| percentage_time_window         | optional(string) | Time window for 201 percentage alerts                                                                              | `"5m"`  |
| adaptive_threshold             | optional(number) | Alert if the 201 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window | `-1`    |
| adaptive_time_window           | optional(string) | Time window for 201 adaptive alerts                                                                                | `"5m"`  |
| adaptive_reference_time_window | optional(string) | Reference Time window                                                                                              | `"3h"`  |


#### `alerts_standard_outbound_response_code`

- ###### `400`

| Inputs                         | Type             | Description                                                                                                                 | Default |
|--------------------------------|------------------|-----------------------------------------------------------------------------------------------------------------------------|---------|
| absolute_threshold             | optional(number) | Alert if the outbound 400 response code errors in application goes beyond 40 in a 5-minute window                           | `500`   |
| absolute_time_window           | optional(string) | Time window for 400 outbound absolute alerts                                                                                | `"5m"`  |
| percentage_threshold           | optional(number) | Alert if the outbound 400 response code errors in application goes beyond 40 percent in a given time window                 | `70`    |
| percentage_time_window         | optional(string) | Time window for 400 outbound percentage alerts                                                                              | `"5m"`  |
| adaptive_threshold             | optional(number) | Alert if the outbound 400 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window | `15`    |
| adaptive_time_window           | optional(string) | Time window for 400 outbound adaptive alerts                                                                                | `"5m"`  |
| adaptive_reference_time_window | optional(string) | Reference Time window                                                                                                       | `"3h"`  |

- ###### `401`

| Inputs                         | Type             | Description                                                                                                                 | Default |
|--------------------------------|------------------|-----------------------------------------------------------------------------------------------------------------------------|---------|
| absolute_threshold             | optional(number) | Alert if the outbound 401 response code errors in application goes beyond 40 in a 5-minute window                           | `100`   |
| absolute_time_window           | optional(string) | Time window for 401 outbound absolute alerts                                                                                | `"5m"`  |
| percentage_threshold           | optional(number) | Alert if the outbound 401 response code errors in application goes beyond 40 percent in a given time window                 | `20`    |
| percentage_time_window         | optional(string) | Time window for 401 outbound percentage alerts                                                                              | `"5m"`  |
| adaptive_threshold             | optional(number) | Alert if the outbound 401 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window | `15`    |
| adaptive_time_window           | optional(string) | Time window for 401 outbound adaptive alerts                                                                                | `"5m"`  |
| adaptive_reference_time_window | optional(string) | Reference Time window                                                                                                       | `"3h"`  |


- ###### `403`

| Inputs                         | Type             | Description                                                                                                                 | Default |
|--------------------------------|------------------|-----------------------------------------------------------------------------------------------------------------------------|---------|
| absolute_threshold             | optional(number) | Alert if the outbound 403 response code errors in application goes beyond 40 in a 5-minute window                           | `100`   |
| absolute_time_window           | optional(string) | Time window for 403 outbound absolute alerts                                                                                | `"5m"`  |
| percentage_threshold           | optional(number) | Alert if the outbound 403 response code errors in application goes beyond 40 percent in a given time window                 | `70`    |
| percentage_time_window         | optional(string) | Time window for 403 outbound percentage alerts                                                                              | `"5m"`  |
| adaptive_threshold             | optional(number) | Alert if the outbound 403 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window | `15`    |
| adaptive_time_window           | optional(string) | Time window for 403 outbound adaptive alerts                                                                                | `"5m"`  |
| adaptive_reference_time_window | optional(string) | Reference Time window                                                                                                       | `"3h"`  |


- ###### `404`

| Inputs                         | Type             | Description                                                                                                                 | Default |
|--------------------------------|------------------|-----------------------------------------------------------------------------------------------------------------------------|---------|
| absolute_threshold             | optional(number) | Alert if the outbound 404 response code errors in application goes beyond 40 in a 5-minute window                           | `500`   |
| absolute_time_window           | optional(string) | Time window for 404 outbound absolute alerts                                                                                | `"5m"`  |
| percentage_threshold           | optional(number) | Alert if the outbound 404 response code errors in application goes beyond 40 percent in a given time window                 | `20`    |
| percentage_time_window         | optional(string) | Time window for 404 outbound percentage alerts                                                                              | `"5m"`  |
| adaptive_threshold             | optional(number) | Alert if the outbound 404 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window | `15`    |
| adaptive_time_window           | optional(string) | Time window for 404 outbound adaptive alerts                                                                                | `"5m"`  |
| adaptive_reference_time_window | optional(string) | Reference Time window                                                                                                       | `"3h"`  |

- ###### `5xx`

| Inputs                         | Type             | Description                                                                                                                       | Default      |
|--------------------------------|------------------|-----------------------------------------------------------------------------------------------------------------------------------|--------------|
| absolute_threshold             | optional(number) | Alert if the outbound 500 response code errors in application goes beyond 40 in a 5-minute window                                 | `40`         |
| absolute_time_window           | optional(string) | Time window for 500 outbound absolute alerts                                                                                      | `"5m"`       |
| percentage_threshold           | optional(number) | Alert if the outbound 500 response code errors in application goes beyond 40 percent in a given time window                       | `40`         |
| percentage_time_window         | optional(string) | Time window for 500 outbound percentage alerts                                                                                    | `"5m"`       |
| adaptive_threshold             | optional(number) | Alert if the outbound 500 response code count in  an application goes beyond 15 percent in a 5min window over last 24-hour window | `15`         |
| adaptive_time_window           | optional(string) | Time window for 500 outbound adaptive alerts                                                                                      | `"5m"`       |
| adaptive_reference_time_window | optional(string) | Reference Time window                                                                                                             | `"3h"`       |
| severity_level                 | optional(string) | Severity level of alert                                                                                                           | `"critical"` |

- ###### `201`

| Inputs                         | Type             | Description                                                                                                                 | Default |
|--------------------------------|------------------|-----------------------------------------------------------------------------------------------------------------------------|---------|
| absolute_threshold             | optional(number) | Alert if the outbound 201 response code errors in application goes beyond 10 in a 5-minute window                           | `-1`    |
| absolute_time_window           | optional(string) | Time window for 201 outbound absolute alerts                                                                                | `"5m"`  |
| percentage_threshold           | optional(number) | Alert if the outbound 201 response code errors in application goes beyond 10 percent in a 5-minute window                   | `-1`    |
| percentage_time_window         | optional(string) | Time window for 201 outbound percentage alerts                                                                              | `"5m"`  |
| adaptive_threshold             | optional(number) | Alert if the outbound 201 response code in  an application goes beyond 15 percent in a 5min window over last 24-hour window | `-1`    |
| adaptive_time_window           | optional(string) | Time window for 201 outbound adaptive alerts                                                                                | `"5m"`  |
| adaptive_reference_time_window | optional(string) | Reference Time window                                                                                                       | `"3h"`  |

#### `alerts_standard_request_count`

| Inputs                         | Type             | Description                            | Default |
|--------------------------------|------------------|----------------------------------------|---------|
| adaptive_threshold             | optional(number) | Alerts based on number of requests     | `30`    |
| adaptive_time_window           | optional(string) | Time window for adaptive request count | `"5m"`  |
| adaptive_reference_time_window | optional(string) | Reference Time window                  | `"3h"`  |

#### `alerts_standard_outbound_request_count`

| Inputs                         | Type             | Description                                     | Default |
|--------------------------------|------------------|-------------------------------------------------|---------|
| adaptive_threshold             | optional(number) | Alerts based on number of outbound requests     | `30`    |
| adaptive_time_window           | optional(string) | Time window for adaptive outbound request count | `"5m"`  |
| adaptive_reference_time_window | optional(string) | Reference Time window                           | `"3h"`  |

#### `alerts_standard_response_count`

| Inputs                        | Type             | Description                                                                                                                     | Default |
|-------------------------------|------------------|---------------------------------------------------------------------------------------------------------------------------------|---------|
| absolute_warning_threshold    | optional(number) | Alert if 95 percentile application response time increases beyond 250ms over a 5-minute window                                  | `0.250` |
| absolute_warning_time_window  | optional(string) | Time window for absolute response time                                                                                          | `"5m"`  |
| absolute_critical_threshold   | optional(number) | Alert if 95 percentile application response time increases beyond 750ms over a 5-minute window                                  | `0.75`  |
| absolute_critical_time_window | optional(string) | Time window for absolute critical response time                                                                                 | `"5m"`  |
| adaptive_threshold            | optional(number) | Alert if 99 percentile application response time increases beyond 15 percent in a last 5-minute window over last 24-hour window | `15`    |
| adaptive_percentile           | optional(number) | The configurable application response percentile                                                                                | `0.99`  |
| time_window                   | optional(string) | Time window for response alerts                                                                                                 | `"5m"`  |
| reference_time_window         | optional(string) | Time window total                                                                                                               | `"3h"`  |


#### `alerts_standard_outbound_response_time`

| Inputs                        | Type             | Description                                                                                                                              | Default |
|-------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------|---------|
| absolute_warning_threshold    | optional(number) | Alert if 95 percentile application outbound response time increases beyond 250ms over a 5-minute window                                  | `-1`    |
| absolute_warning_time_window  | optional(string) | Time window for absolute warning outbound response time                                                                                  | `"5m"`  |
| absolute_critical_threshold   | optional(number) | Alert if 95 percentile application outbound  response time increases beyond 750ms over a 5-minute window                                 | `-1`    |
| absolute_critical_time_window | optional(string) | Time window for absolute critical outbound response time                                                                                 | `"5m"`  |
| adaptive_threshold            | optional(number) | Alert if 99 percentile application outbound response time increases beyond 15 percent in a last 5-minute window over last 24-hour window | `-1`    |
| adaptive_percentile           | optional(number) | The configurable application outbound response percentile                                                                                | `0.99`  |
| time_window                   | optional(string) | Time window for outbound response time                                                                                                   | `"5m"`  |
| reference_time_window         | optional(string) | Time window total                                                                                                                        | `"3h"`  |

#### `custom_alerts`

| Inputs         | Type             | Description                                                        | Default |
|----------------|------------------|--------------------------------------------------------------------|---------|
| name           | string           | Custom alert if user_created events goes below threshold for 5 min | `""`    |
| description    | string           | Custom alert if user_created events goes below threshold for 5 min | `""`    |
| alert_rule     | string           | Metric Name exposed by /metric endpoint                            | `""`    |
| sum_by_label   | optional(string) | Metric events key; can be empty string                             | `""`    |
| percentile     | optional(number) | Percentile is useful for histogram queries                         | `0.0`   |
| label_value    | optional(string) | Metric Event Name; can be empty string                             | `""`    |
| query_operator | optional(string) | Query Operator                                                     | `">"`   |
| time_window    | string           | Time window for custom alerts                                      | `""`    |
| threshold      | string           | Threshold                                                          | `""`    |
| severity       | string           | Severity level of alert                                            | `""`    |


#### `path_method_response_code_alerts`

| Inputs                         | Type             | Description                                                                                                                           | Default  |
|--------------------------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------|----------|
| path                           | optional(string) | Custom path given by user                                                                                                             | `".*"`   |
| method                         | optional(string) | Custom method given by user                                                                                                           | `".*"`   |
| response_code                  | string           | Response Code for different alerts                                                                                                    |
| severity_level                 | optional(string) | Severity level of alert                                                                                                               | critical |
| absolute_threshold             | optional(number) | Alert if the response code errors in application goes beyond absolute threshold in absolute time window                               | `-1`     |
| absolute_time_window           | optional(string) | Time window for absolute response code alerts                                                                                         | `"5m"`   |
| percentage_threshold           | optional(number) | Alert if the response code errors in application goes beyond percentage threshold percent in percentage time window                   | `-1`     |
| percentage_time_window         | optional(string) | Time window for percentage response code alerts                                                                                       | `"5m"`   |
| adaptive_threshold             | optional(number) | Alert if the response code count in an application goes beyond 15 percent in adaptive time window over adaptive reference time window | `-1`     |
| adaptive_time_window           | optional(string) | Time window for adaptive response code alerts                                                                                         | `"5m"`   |
| adaptive_reference_time_window | optional(string) | Reference Time window                                                                                                                 | `"3h"`   |     

#### `path_method_request_count_alerts`

| Inputs                                     | Type             | Description                                                                                                                          | Default  |
|--------------------------------------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------|----------|
| path                                       | optional(string) | Custom path given by user                                                                                                            | `".*"`   |
| method                                     | optional(string) | Custom method given by user                                                                                                          | `".*"`   |
| severity_level                             | optional(string) | Severity level of alert                                                                                                              | critical |
| adaptive_threshold                         | optional(number) | Alert if the response code count in an application goes lower 15 percent in adaptive time window over adaptive reference time window | `-1`     |
| adaptive_time_window                       | optional(string) | Time window for adaptive request count alerts                                                                                        | `"5m"`   |
| adaptive_reference_time_window             | optional(string) | Reference Time window                                                                                                                | `"3h"`   |

#### `path_method_response_time_alerts`

| Inputs                         | Type             | Description                                                                                                                           | Default  |
|--------------------------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------|----------|
| path                           | optional(string) | Custom path given by user                                                                                                             | `".*"`   |
| method                         | optional(string) | Custom method given by user                                                                                                           | `".*"`   |
| severity_level                 | optional(string) | Severity level of alert                                                                                                               | critical |
| absolute_threshold             | number           | Alert if the response code errors in application goes beyond absolute threshold in absolute time window                               | `-1`     |
| absolute_time_window           | optional(string) | Time window for absolute response time alerts                                                                                         | `"5m"`   |
| absolute_percentile            | optional(number) | percentile given by the user                                                                                                          | `-1`     |
| adaptive_threshold             | optional(number) | Alert if the response code count in an application goes beyond 15 percent in adaptive time window over adaptive reference time window | `-1`     |
| adaptive_percentile            | optional(number) | The configurable application response percentile                                                                                      | `-1`     |
| adaptive_time_window           | optional(string) | Time window for adaptive response time alerts                                                                                         | `"5m"`   |
| adaptive_reference_time_window | optional(string) | Reference Time window                                                                                                                 | `"3h"`   |     

#### `path_method_outbound_response_code_alerts`

| Inputs                         | Type             | Description                                                                                                                           | Default  |
|--------------------------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------|----------|
| path                           | optional(string) | Custom path given by user                                                                                                             | `".*"`   |
| method                         | optional(string) | Custom method given by user                                                                                                           | `".*"`   |
| response_code                  | string           | Response Code for different alerts                                                                                                    |
| severity_level                 | optional(string) | Severity level of alert                                                                                                               | critical |
| absolute_threshold             | optional(number) | Alert if the response code errors in application goes beyond absolute threshold in absolute time window                               | `-1`     |
| absolute_time_window           | optional(string) | Time window for absolute outbound response code alerts                                                                                | `"5m"`   |
| percentage_threshold           | optional(number) | Alert if the response code errors in application goes beyond percentage threshold percent in percentage time window                   | `-1`     |
| percentage_time_window         | optional(string) | Time window for percentage outbound response code alerts                                                                              | `"5m"`   |
| adaptive_threshold             | optional(number) | Alert if the response code count in an application goes beyond 15 percent in adaptive time window over adaptive reference time window | `-1`     |
| adaptive_time_window           | optional(string) | Time window for adaptive outbound response code alerts                                                                                | `"5m"`   |
| adaptive_reference_time_window | optional(string) | Reference Time window                                                                                                                 | `"3h"`   |     

#### `path_method_outbound_request_count_alerts`

| Inputs                                     | Type             | Description                                                                                                                           | Default  |
|--------------------------------------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------|----------|
| path                                       | optional(string) | Custom path given by user                                                                                                             | `".*"`   |
| method                                     | optional(string) | Custom method given by user                                                                                                           | `".*"`   |
| severity_level                             | optional(string) | Severity level of alert                                                                                                               | critical |
| adaptive_threshold_lower_bound             | optional(number) | Alert if the response code count in an application goes lower 15 percent in adaptive time window over adaptive reference time window  | `-1`     |
| adaptive_lower_bound_time_window           | optional(string) | Time window for adaptive lower bound                                                                                                  | `"5m"`   |
| adaptive_lower_bound_reference_time_window | optional(string) | Reference Time window                                                                                                                 | `"3h"`   |  
| adaptive_threshold_upper_bound             | optional(number) | Alert if the response code count in an application goes beyond 15 percent in adaptive time window over adaptive reference time window | `-1`     |
| adaptive_upper_bound_time_window           | optional(string) | Time window for adaptive upper bound                                                                                                  | `"5m"`   |
| adaptive_upper_bound_reference_time_window | optional(string) | Reference Time window                                                                                                                 | `"3h"`   |       

#### `path_method_outbound_response_time_alerts`

| Inputs                         | Type             | Description                                                                                                                           | Default  |
|--------------------------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------|----------|
| path                           | optional(string) | Custom path given by user                                                                                                             | `".*"`   |
| method                         | optional(string) | Custom method given by user                                                                                                           | `".*"`   |
| severity_level                 | optional(string) | Severity level of alert                                                                                                               | critical |
| absolute_threshold             | number           | Alert if the response code errors in application goes beyond absolute threshold in absolute time window                               | `-1`     |
| absolute_time_window           | optional(string) | Time window for absolute outbound response time alerts                                                                                | `"5m"`   |
| absolute_percentile            | optional(number) | percentile given by the user                                                                                                          | `-1`     |
| adaptive_threshold             | optional(number) | Alert if the response code count in an application goes beyond 15 percent in adaptive time window over adaptive reference time window | `-1`     |
| adaptive_percentile            | optional(number) | The configurable application response percentile                                                                                      | `-1`     |
| adaptive_time_window           | optional(string) | Time window for adaptive outbound response time alerts                                                                                | `"5m"`   |
| adaptive_reference_time_window | optional(string) | Reference Time window                                                                                                                 | `"3h"`   |  
