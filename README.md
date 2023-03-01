# zopsmart-helm
Common helm chart for micro service deployment. Creates Deployment, Services, HPA, ServiceMonitor, Alerts etc.

This helm chart can be used by kubectl command to manually deploy an application to a cluster. Continous deployment systems 
like harness can use this helm chart to deploy any service to EKS cluster.


Install/ Upgrade using the below command
```
helm upgrade --install {service-name} ./service/ -f values.yaml -n {namespace}
```
