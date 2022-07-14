# Virtual node
![Version: 0.0.1](https://img.shields.io/badge/Version-0.0.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.2.1](https://img.shields.io/badge/AppVersion-1.2.1-informational?style=flat-square)

TL;DR

```commandline
helm repo add anonybit https://anonybit-io.github.io/public-helm-charts
helm install vmnode01 anonybit-public/vmnode -n vmnodes --create-namespace
```

Deploy with params
```commandline
helm template vmnode11 vmnode -n vmnodes-bdika \
    --set ingress.subdomain="subdomain.for.vmnode.com" \
    --set job.serverAddress='https://api.server.of.anonybit.io' \
    --set job.apiKey='SOME_API_KEY' \
    --set job.image.tag='key-generator-0.1' --set job.nid='NETWORK_ID'
```

## Autoscaling
Autoscaling is disabled by default, to enable it, make sure that cluster has metrics-server.
```
--set deployment.autoscaling.enabled=true
```

To deploy [metrics-server](https://github.com/kubernetes-sigs/metrics-server)
```commandline
helm repo add metrics-server https://kubernetes-sigs.github.io/metrics-server/
helm upgrade --install metrics-server metrics-server/metrics-server
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| deployment.annotations | object | `{}` |  |
| deployment.autoscaling.enabled | bool | `true` |  |
| deployment.autoscaling.maxReplicas | int | `100` |  |
| deployment.autoscaling.minReplicas | int | `2` |  |
| deployment.autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| deployment.autoscaling.targetMemoryUtilizationPercentage | int | `80` |  |
| deployment.containers[0].image.pullPolicy | string | `"IfNotPresent"` |  |
| deployment.containers[0].image.repository | string | `"anonybit/vmnode"` |  |
| deployment.containers[0].image.tag | string | `"1.2.1"` |  |
| deployment.containers[0].livenessProbe.failureThreshold | int | `3` |  |
| deployment.containers[0].livenessProbe.httpGet.path | string | `"/"` |  |
| deployment.containers[0].livenessProbe.httpGet.port | string | `"http"` |  |
| deployment.containers[0].livenessProbe.httpGet.scheme | string | `"HTTP"` |  |
| deployment.containers[0].livenessProbe.initialDelaySeconds | int | `30` |  |
| deployment.containers[0].livenessProbe.periodSeconds | int | `10` |  |
| deployment.containers[0].livenessProbe.successThreshold | int | `1` |  |
| deployment.containers[0].livenessProbe.timeoutSeconds | int | `15` |  |
| deployment.containers[0].name | string | `"vmnode"` |  |
| deployment.containers[0].ports[0].containerPort | int | `80` |  |
| deployment.containers[0].ports[0].name | string | `"http"` |  |
| deployment.containers[0].ports[0].protocol | string | `"TCP"` |  |
| deployment.containers[0].readinessProbe.failureThreshold | int | `30` |  |
| deployment.containers[0].readinessProbe.httpGet.path | string | `"/"` |  |
| deployment.containers[0].readinessProbe.httpGet.port | string | `"http"` |  |
| deployment.containers[0].readinessProbe.httpGet.scheme | string | `"HTTP"` |  |
| deployment.containers[0].readinessProbe.initialDelaySeconds | int | `10` |  |
| deployment.containers[0].readinessProbe.periodSeconds | int | `10` |  |
| deployment.containers[0].readinessProbe.successThreshold | int | `1` |  |
| deployment.containers[0].readinessProbe.timeoutSeconds | int | `20` |  |
| deployment.containers[0].resources.requests.cpu | string | `"200m"` |  |
| deployment.containers[0].resources.requests.memory | string | `"512Mi"` |  |
| deployment.containers[0].volumeMounts[0].mountPath | string | `"/tmp/"` |  |
| deployment.containers[0].volumeMounts[0].name | string | `"log-storage"` |  |
| deployment.dnsConfig.options[0].name | string | `"single-request-reopen"` |  |
| deployment.dnsPolicy | string | `"ClusterFirst"` |  |
| deployment.imagePullSecrets | object | `{}` |  |
| deployment.labels | object | `{}` |  |
| deployment.progressDeadlineSeconds | int | `600` |  |
| deployment.replicaCount | int | `2` |  |
| deployment.restartPolicy | string | `"Always"` |  |
| deployment.revisionHistoryLimit | int | `10` |  |
| deployment.strategy.rollingUpdate.maxSurge | string | `"15%"` |  |
| deployment.strategy.rollingUpdate.maxUnavailable | int | `0` |  |
| deployment.strategy.type | string | `"RollingUpdate"` |  |
| deployment.terminationGracePeriodSeconds | int | `30` |  |
| ingress.annotations."kubernetes.io/ingress.class" | string | `"nginx"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/force-ssl-redirect" | string | `"false"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/rewrite-target" | string | `"/"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/ssl-redirect" | string | `"false"` |  |
| ingress.enabled | bool | `true` |  |
| ingress.hosts[0].host | string | `nil` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"ImplementationSpecific"` |  |
| ingress.hosts[0].paths[0].serviceName | string | `nil` |  |
| ingress.hosts[0].paths[0].servicePort | int | `80` |  |
| ingress.labels | object | `{}` |  |
| ingress.subdomain | string | `"demo.anonybit.io"` |  |
| ingress.tls | list | `[]` |  |
| job.amountOfKeys | string | `"1"` |  |
| job.apiKey | string | `nil` |  |
| job.image.repository | string | `"anonybit/vmnode"` |  |
| job.image.tag | string | `"key-generator-0.1"` |  |
| job.lbAddress | string | `nil` |  |
| job.nid | string | `nil` |  |
| job.run | bool | `true` |  |
| job.serverAddress | string | `"https://api.anonybit.io"` |  |
| service.enabled | bool | `true` |  |
| service.services[0].annotations | object | `{}` |  |
| service.services[0].labels | object | `{}` |  |
| service.services[0].name | string | `nil` |  |
| service.services[0].ports[0].name | string | `"http"` |  |
| service.services[0].ports[0].port | int | `80` |  |
| service.services[0].ports[0].protocol | string | `"TCP"` |  |
| service.services[0].ports[0].targetPort | int | `80` |  |

