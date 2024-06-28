# Service 

Installs the service, a collection of kubernetes manifest for Deployment, Services, HPA, PDB, ServiceMonitor, Alerts, etc.

## Prerequisites

- Kubernetes 1.19+
- Helm 3+

## Get Helm Repository Info

```console
helm repo add kops-dev https://kops-dev.github.io/helm
helm repo update
```

_See [`helm repo`](https://helm.sh/docs/helm/helm_repo/) for command documentation._

## Install Helm Chart

```console
helm install [RELEASE_NAME] kops-dev/service
```

_See [configuration](#configuration) below._

_See [helm install](https://helm.sh/docs/helm/helm_install/) for command documentation._

## Uninstall Helm Chart

```console
helm uninstall [RELEASE_NAME]
```

This removes all the Kubernetes components associated with the chart and deletes the release.

_See [helm uninstall](https://helm.sh/docs/helm/helm_uninstall/) for command documentation._

# Configuration

| Inputs                             | Type    | Description                                                                                                         | Default                              |
|------------------------------------|---------|---------------------------------------------------------------------------------------------------------------------|--------------------------------------|
| app_secrets                        | boolean | Boolean whether to mount csi secrets on the container                                                               | `false`                              |
| cliService                         | boolean | Whether application is a CLI service                                                                                | `false`                              |
| env                                | map     | Environment Variables can be provided to the container                                                              | `eg APP_NAME: hello-api`             |
| envFrom.configmaps                 | list    | List of Configmaps from which env should be mounted on to containers                                                | `[]`                                 |
| envFrom.secrets                    | list    | List of secrets from which env should be mounted on to containers                                                   | `[]`                                 |
| heartbeatURL                       | string  | Heartbeat URL of the service                                                                                        | `""`                                 |
| httpPort                           | number  | HTTP Port on which container runs its services                                                                      | `8000`                               |
| image                              | string  | Docker container image with tag                                                                                     | `ghcr.io/kops-dev/sample-api:latest` |
| imagePullSecrets                   | list    | configuration to specify secrets that contain credentials for pulling container images from private registries      | `[]`                                 |
| livenessProbe.enable               | boolean | Whether liveness Probe should be configured on the container or not                                                 | `false`                              |
| livenessProbe.initialDelaySeconds  | number  | Specifies how long Kubernetes should wait after the container starts before it begins liveness probes (in seconds)  | `3`                                  |
| livenessProbe.timeoutSeconds       | number  | Specifies the number of seconds after which the probe times out                                                     | `3`                                  |
| livenessProbe.periodSeconds        | number  | Specifies how often (in seconds) to perform the liveness probe                                                      | `10`                                 |
| livenessProbe.failureThreshold     | number  | Specifies the number of consecutive failures needed to mark the probe as failed                                     | `3`                                  |
| maxCPU                             | string  | Specify the maximum amount of CPU that the container is limited to use                                              | `"500m"`                             |
| maxMemory                          | string  | Specify the maximum amount of Memory that the container is limited to use                                           | `"512Mi"`                            |
| maxReplicas                        | number  | Specify maximum number of pod replicas that the autoscaler can scale up to in response to increased load            | `4`                                  |
| metricsPort                        | number  | Metrics port for scraping the metrics from container                                                                | `2121`                               |
| metricsScrapeInterval              | string  | Time interval that metrics will be scraped                                                                          | `"30s"`                              |
| minAvailable                       | number  | Minimum number of pods that must be available during voluntary disruptions                                          | `1`                                  |
| minCPU                             | string  | Specify the minimum amount of CPU that the container requires                                                       | `"250m"`                             |
| minMemory                          | string  | Specify the minimum amount of Memory that the container requires                                                    | `"128Mi"`                            |
| minReplicas                        | number  | Specify the baseline number of identical pods allowed to be running                                                 | `2`                                  |
| name                               | string  | Name of the service                                                                                                 | `"hello-api"`                        |
| ports                              | map     | Provide the ports on which container runs its services                                                              | `null`                               |
| readinessProbe.enable              | boolean | Whether Readiness Probe should be configured on the container or not                                                | `false`                              |
| readinessProbe.initialDelaySeconds | number  | Specifies how long Kubernetes should wait after the container starts before it begins readiness probes (in seconds) | `3`                                  |
| readinessProbe.timeoutSeconds      | number  | Specifies the number of seconds after which the probe times out                                                     | `3`                                  |
| readinessProbe.periodSeconds       | number  | Specifies how often (in seconds) to perform the readiness probe                                                     | `10`                                 |
| readinessProbe.failureThreshold    | number  | Specifies the number of consecutive failures needed to mark the probe as failed                                     | `3`                                  |
| replicaCount                       | number  | Number of replicas to run                                                                                           | `2`                                  |
| volumeMounts.configmaps            | list    | List of Configmaps with name and mount-path to be mounted into the container to inject configuration data           | `[]`                                 |
| volumeMounts.secrets               | list    | List of Secrets with name and mount-path to be mounted into the container to inject sensitive information           | `[]`                                 |


### Note:
To refer readme related to Alerts in Helm template, [click here](ALERTS.md)

