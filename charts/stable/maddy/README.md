# maddy

![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-informational?style=flat-square) ![AppVersion: 0.4.4](https://img.shields.io/badge/AppVersion-0.4.4-informational?style=flat-square)

Composable all-in-one mail server

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## Source Code

* <https://github.com/foxcpp/maddy>

## Requirements

Kubernetes: `>=1.16.0-0`

## Dependencies

| Repository | Name | Version |
|------------|------|---------|
| https://library-charts.k8s-at-home.com | common | 2.2.0 |

## TL;DR

```console
helm repo add k8s-at-home https://k8s-at-home.com/charts/
helm repo update
helm install maddy k8s-at-home/maddy
```

## Installing the Chart

To install the chart with the release name `maddy`

```console
helm install maddy k8s-at-home/maddy
```

## Uninstalling the Chart

To uninstall the `maddy` deployment

```console
helm uninstall maddy
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common/values.yaml) from the [common library](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install maddy \
  --set env.TZ="America/New York" \
    k8s-at-home/maddy
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install maddy k8s-at-home/maddy -f values.yaml
```

## Custom configuration

### TLS certificates

This chart can make use of an existing cert-manager deployment to generate TLS certificates dynamically.
See the available parameters under `pki.certManager` in `values.yaml`.

To bring your own certificate, see: [TLS certificates](https://maddy.email/tutorials/setting-up/#tls-certificates).
Assuming use of the default values, you must create a secret called `acme-crt-secret` with the following data:

```yaml
...
data:
  tls.crt: AB..==
  tls.key: CD..==
```

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| config.config | string | `...` |  |
| config.mode | string | `"values"` |  |
| env.MADDY_HOSTNAME | string | `mx.example.org` | MX hostname |
| env.MADDY_DOMAIN | string | `example.org` | Domain to handle messages for |
| extraVolumeMounts[0].mountPath | string | `/etc/ssl/` |  |
| extraVolumeMounts[0].name | string | `tls-cert` |  |
| extraVolumes[0].name | string | `tls-cert` |  |
| extraVolumes[0].secret.secretName | string | `acme-crt-secret` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"foxcpp/maddy"` |  |
| image.tag | string | `0.4.4` |  |
| ingress.enabled | bool | `false` |  |
| persistence.data.accessMode | string | `ReadWriteOnce` |  |
| persistence.data.enabled | bool | `true` |  |
| persistence.data.mountPath | string | `/data` |  |
| persistence.data.size | string | `5Gi` |  |
| pki.certManager.enabled | bool | `false` |  |
| pki.certManager.issuerKind | string | `ClusterIssuer` |  |
| pki.certManager.issuerName | string | `letsencrypt-prod` |  |
| service.port.name | string | `smtprelay` |  |
| service.port.port | int | `25` |  |
| service.additionalServices[0].name | string | `imap` |  |
| service.additionalServices[0].port | int | `143` |  |
| service.additionalServices[1].name | string | `smtp` |  |
| service.additionalServices[1].port | int | `587` |  |
| service.additionalServices[2].name | string | `imaptls` |  |
| service.additionalServices[2].port | int | `993` |  |
| strategy.type | string | `"Recreate"` |  |

## Changelog

All notable changes to this application Helm chart will be documented in this file but does not include changes from our common library. To read those click [here](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common#changelog).

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

### [1.0.0]

#### Added

* New chart

#### Changed

* N/A

#### Removed

* N/A

[1.0.0]: #1.0.0

## Support

* See the [Docs](https://docs.k8s-at-home.com/our-helm-charts/getting-started/)
* Open an [issue](https://github.com/k8s-at-home/charts/issues/new/choose)
* Ask a [question](https://github.com/k8s-at-home/organization/discussions)
* Join our [Discord](https://discord.gg/sTMX7Vh) community
