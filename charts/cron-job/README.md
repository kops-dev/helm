# Service Module
- The `cron-job` module helps you to create CronJob, Services, ServiceMonitor, Alerts, etc.

##### Install/ Upgrade using the below command
```
helm upgrade --install {cron-name} ./cron-job/ -f values.yaml -n {namespace}
```

####  `Values`

| Inputs                             | Type    | Description                                                                                                         | Default                              |
|------------------------------------|---------|---------------------------------------------------------------------------------------------------------------------|--------------------------------------|
| app_secrets                        | boolean | Boolean whether to mount csi secrets on the container                                                               | `false`                              |
| env                                | map     | Environment Variables can be provided to the container                                                              | `eg APP_NAME: hello-api`             |
| envFrom.configmaps                 | list    | List of Configmaps from which env should be mounted on to containers                                                | `[]`                                 |
| envFrom.secrets                    | list    | List of secrets from which env should be mounted on to containers                                                   | `[]`                                 |
| image                              | string  | Docker container image with tag                                                                                     | `ghcr.io/kops-dev/sample-api:latest` |
| maxCPU                             | string  | Specify the maximum amount of CPU that the container is limited to use                                              | `"500m"`                             |
| maxMemory                          | string  | Specify the maximum amount of Memory that the container is limited to use                                           | `"512Mi"`                            |
| metricsPort                        | number  | Metrics port for scraping the metrics from container                                                                | `2121`                               |
| metricsScrapeInterval              | string  | Time interval that metrics will be scraped                                                                          | `"30s"`                              |
| minCPU                             | string  | Specify the minimum amount of CPU that the container requires                                                       | `"250m"`                             |
| minMemory                          | string  | Specify the minimum amount of Memory that the container requires                                                    | `"128Mi"`                            |
| name                               | string  | Name of the service                                                                                                 | `"hello-api"`                        |
| volumeMounts.configmaps            | list    | List of Configmaps with name and mount-path to be mounted into the container to inject configuration data           | `[]`                                 |
| volumeMounts.secrets               | list    | List of Secrets with name and mount-path to be mounted into the container to inject sensitive information           | `[]`                                 |

### Note:
To refer readme related to Alerts in Helm template, [click here](ALERTS.md)
