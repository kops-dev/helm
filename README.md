# Helm Module
- Helm helps you manage Kubernetes applications. `Helm Charts` help you define, install, and upgrade even the most complex Kubernetes application. Charts are easy to create, version, share, and publish.
- The `helm` module helps you to create Deployment, Services, HPA, ServiceMonitor, Alerts, etc. 

This helm chart can be used by kubectl command to manually deploy an application to a cluster. Continuous deployment systems 
like harness can use this helm chart to deploy any service to EKS/AKS/GKE cluster.


##### Install/ Upgrade using the below command
```
helm upgrade --install {service-name} ./service/ -f values.yaml -n {namespace}
```

####  `Values`

| Inputs                                                                    | Type             | Description                                                                                                                              | Default                    |
|---------------------------------------------------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------|----------------------------|
| cliService                                                                | optional(bool)   | Whether application is a CLI service                                                                                                     | `false`                    |
| cluster_name                                                              | string           | Name of the Kubernetes cluster                                                                                                           |                            |
| concurrencyPolicy                                                         | optional(string) | Concurrency policy                                                                                                                       | `"Replace"`                |
| env.cloud                                                                 | optional(string) | Cloud name                                                                                                                               | `"GCP"`                    |
| env.HTTP_PORT                                                             | optional(number) | HTTP port                                                                                                                                | `8000`                     |
| env.TRACER_URL                                                            | optional(string) | Tracer url                                                                                                                               | `""`                       |
| env.TRACER_EXPORTER                                                       | optional(string) | Tracer exporter                                                                                                                          | `""`                       |
| DB_DIALECT                                                                | string           | DB type(ex - mysql, postgresql are valid)                                                                                                | `""`                       |
| default_severity                                                          | string           | Default severity level that alerts will be tagged to                                                                                     | `critical`                 |
| heartbeatURL                                                              | optional(string) | Heartbeat URL                                                                                                                            | `"/.well-known/heartbeat"` |
| hpa_cpu_limit                                                             | optional(number) | HPA CPU limit                                                                                                                            | `80`                       |
| hpa_memory_limit                                                          | optional(number) | HPA Memory limit                                                                                                                         | `80`                       |
| httpPort                                                                  | optional(number) | Port on which container runs its services                                                                                                | `8000`                     |
| image                                                                     | string           | Docker container image with tag                                                                                                          |                            |
| kubernetes_version                                                        | optional(float)  | Kubernetes version used to create the cluster                                                                                            | `1.24`                     |
| maxCPU                                                                    | optional(string) | Maximum CPU resources                                                                                                                    | `"500m"`                   |
| maxMemory                                                                 | optional(string) | Maximum Memory resources                                                                                                                 | `"512Mi"`                  |
| maxReplicas                                                               | optional(number) | Maximum replicas                                                                                                                         | `4`                        |
| metricsPort                                                               | optional(number) | Metrics port on which container runs its services                                                                                        | `2121`                     |
| metricsScrapeInterval                                                     | optional(string) | Time interval that metrics will be scraped                                                                                               | `"30s"`                    |
| minCPU                                                                    | optional(string) | Minimum CPU resources                                                                                                                    | `"250m"`                   |
| minMemory                                                                 | optional(string) | Minimum Memory resources                                                                                                                 | `"128Mi"`                  |
| minReplicas                                                               | optional(number) | Minimum replicas                                                                                                                         | `2`                        |
| name                                                                      | optional(string) | Name of the service                                                                                                                      | `"hello-api"`              |
| replicaCount                                                              | optional(number) | Number of replicas to run                                                                                                                | `2`                        |
| schedule                                                                  | optional(string) | Cron job schedule                                                                                                                        | `""`                       |
| suspend                                                                   | optional(bool)   | Cron job suspend                                                                                                                         | `false`                    |
