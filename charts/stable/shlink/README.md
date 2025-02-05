# shlink

![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-informational?style=flat-square) ![AppVersion: 2.6.2](https://img.shields.io/badge/AppVersion-2.6.2-informational?style=flat-square)

A self-hosted and PHP-based URL shortener application with CLI and REST interfaces

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## Source Code

* <https://github.com/shlinkio/shlink>

## Requirements

Kubernetes: `>=1.16.0-0`

## Dependencies

| Repository | Name | Version |
|------------|------|---------|
| https://charts.bitnami.com/bitnami | mariadb | 9.3.9 |
| https://charts.bitnami.com/bitnami | postgresql | 10.4.0 |
| https://library-charts.k8s-at-home.com | common | 2.5.0 |

## TL;DR

```console
helm repo add k8s-at-home https://k8s-at-home.com/charts/
helm repo update
helm install shlink k8s-at-home/shlink
```

## Installing the Chart

To install the chart with the release name `shlink`

```console
helm install shlink k8s-at-home/shlink
```

## Uninstalling the Chart

To uninstall the `shlink` deployment

```console
helm uninstall shlink
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common/values.yaml) from the [common library](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install shlink \
  --set env.TZ="America/New York" \
    k8s-at-home/shlink
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install shlink k8s-at-home/shlink -f values.yaml
```

## Custom configuration

N/A

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| env | object | `{}` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"shlinkio/shlink"` |  |
| image.tag | string | `"2.6.2"` |  |
| ingress.enabled | bool | `false` |  |
| mariadb.architecture | string | `"standalone"` |  |
| mariadb.auth.database | string | `"shlink"` |  |
| mariadb.auth.password | string | `"shlink-pass"` |  |
| mariadb.auth.rootPassword | string | `"shlinkrootpass"` |  |
| mariadb.auth.username | string | `"shlink"` |  |
| mariadb.enabled | bool | `false` |  |
| mariadb.primary.persistence.enabled | bool | `false` |  |
| persistence.data.emptyDir.enabled | bool | `false` |  |
| persistence.data.enabled | bool | `false` |  |
| persistence.data.mountPath | string | `"/etc/shlink/data"` |  |
| persistence.params.emptyDir.enabled | bool | `false` |  |
| persistence.params.enabled | bool | `false` |  |
| persistence.params.mountPath | string | `"/etc/shlink/config/params"` |  |
| postgresql.enabled | bool | `false` |  |
| postgresql.persistence.enabled | bool | `false` |  |
| postgresql.postgresqlDatabase | string | `"shlink"` |  |
| postgresql.postgresqlPassword | string | `"shlink-pass"` |  |
| postgresql.postgresqlUsername | string | `"shlink"` |  |
| service.port.port | int | `8080` |  |
| strategy.type | string | `"Recreate"` |  |

## Changelog

All notable changes to this application Helm chart will be documented in this file but does not include changes from our common library. To read those click [here](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common#changelog).

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

### [1.0.0]

#### Added

- Initial version

[1.0.0]: #100

## Support

- See the [Docs](https://docs.k8s-at-home.com/our-helm-charts/getting-started/)
- Open an [issue](https://github.com/k8s-at-home/charts/issues/new/choose)
- Ask a [question](https://github.com/k8s-at-home/organization/discussions)
- Join our [Discord](https://discord.gg/sTMX7Vh) community

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.5.0](https://github.com/norwoodj/helm-docs/releases/v1.5.0)
