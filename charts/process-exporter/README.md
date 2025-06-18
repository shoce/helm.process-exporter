# Process exporter Helm Chart

## Chart Details

Helm Chart for [process exporter](https://github.com/ncabatoff/process-exporter)

## Parameters

### Common

| Name               | Description                                                                           | Value |
| ------------------ | ------------------------------------------------------------------------------------- | ----- |
| `nameOverride`     | String to partially override gitea.fullname template (will maintain the release name) | `""`  |
| `fullnameOverride` | String to fully override gitea.fullname template                                      | `""`  |
| `extraDeploy`      | Array of extra objects to deploy with the release                                     | `[]`  |

### Process exporter

| Name                                 | Description                                                                                                                                         | Value                                                                     |
| ------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `image.registry`                     | Process exporter image registry                                                                                                                     | `docker.io`                                                               |
| `image.repository`                   | Process exporter image repository                                                                                                                   | `ncabatoff/process-exporter`                                              |
| `image.tag`                          | Process exporter image tag                                                                                                                          | `.Chart.AppVersion`                                                       |
| `image.digest`                       | Image digest in the way sha256:aa.... Please note this parameter, if set, will override the tag                                                     | `sha256:6f0549dc24e97a51a3a3524271082cfa2f44352d96fd6a038bfa00659470639a` |
| `image.pullPolicy`                   | Process exporter image pull policy                                                                                                                  | `IfNotPresent`                                                            |
| `resources`                          | Set container requests and limits for different resources like CPU or memory                                                                        | `{}`                                                                      |
| `config.threads`                     | specifies if metrics will be broken down by thread name as well as group name.                                                                      | `false`                                                                   |
| `config.nameMatchers`                | Check [configuration and group naming](https://github.com/ncabatoff/process-exporter/tree/master?tab=readme-ov-file#configuration-and-group-naming) | `[]`                                                                      |
| `nodeSelector`                       | Process exporter node labels for pod assignment                                                                                                     | `{}`                                                                      |
| `tolerations`                        | Process exporter tolerations for pod assignment                                                                                                     | `[]`                                                                      |
| `affinity`                           | Process exporter affinity for pod assignment                                                                                                        | `{}`                                                                      |
| `livenessProbe.enabled`              | Enable livenessProbe on Process exporter containers                                                                                                 | `true`                                                                    |
| `livenessProbe.initialDelaySeconds`  | Initial delay seconds for livenessProbe                                                                                                             | `30`                                                                      |
| `livenessProbe.periodSeconds`        | Period seconds for livenessProbe                                                                                                                    | `30`                                                                      |
| `livenessProbe.timeoutSeconds`       | Timeout seconds for livenessProbe                                                                                                                   | `30`                                                                      |
| `livenessProbe.failureThreshold`     | Failure threshold for livenessProbe                                                                                                                 | `5`                                                                       |
| `livenessProbe.successThreshold`     | Success threshold for livenessProbe                                                                                                                 | `1`                                                                       |
| `readinessProbe.enabled`             | Enable readinessProbe on Process exporter containers                                                                                                | `true`                                                                    |
| `readinessProbe.initialDelaySeconds` | Initial delay seconds for readinessProbe                                                                                                            | `30`                                                                      |
| `readinessProbe.periodSeconds`       | Period seconds for readinessProbe                                                                                                                   | `30`                                                                      |
| `readinessProbe.timeoutSeconds`      | Timeout seconds for readinessProbe                                                                                                                  | `30`                                                                      |
| `readinessProbe.failureThreshold`    | Failure threshold for readinessProbe                                                                                                                | `5`                                                                       |
| `readinessProbe.successThreshold`    | Success threshold for readinessProbe                                                                                                                | `1`                                                                       |
| `extraArgs`                          | Additional container arguments                                                                                                                      | `[]`                                                                      |

### Traffic exposure

| Name           | Description                  | Value       |
| -------------- | ---------------------------- | ----------- |
| `service.type` | Kubernetes service type      | `ClusterIP` |
| `service.port` | Kubernetes service HTTP port | `9256`      |

### Metrics

| Name                               | Description                                                          | Value  |
| ---------------------------------- | -------------------------------------------------------------------- | ------ |
| `serviceMonitor.enabled`           | Specify if a ServiceMonitor will be deployed for Prometheus Operator | `true` |
| `serviceMonitor.metricRelabelings` | MetricRelabelConfigs to apply to samples before ingestion            | `[]`   |

### Other

| Name                    | Description                                                              | Value  |
| ----------------------- | ------------------------------------------------------------------------ | ------ |
| `serviceAccount.create` | Specifies whether a ServiceAccount should be created                     | `true` |
| `securityContext`       | Process exporter privilege and access control settings for the container | `{}`   |
