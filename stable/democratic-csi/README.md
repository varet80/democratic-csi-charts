# democratic-csi

csi storage for container orchestration systems

![Version: 0.13.5](https://img.shields.io/badge/Version-0.13.5-informational?style=flat-square) ![AppVersion: 1.0](https://img.shields.io/badge/AppVersion-1.0-informational?style=flat-square)

# Description
[democratic-csi](https://github.com/democratic-csi/democratic-csi) implements
the [csi](https://github.com/container-storage-interface/spec/blob/master/spec.md)
spec to facilitate stateful workloads.

Currently `democratic-csi` integrates with the following storage systems:

- [TrueNAS](https://www.truenas.com)
- ZFS on Linux (ZoL, ie: generic Ubuntu server)
- [Synology](https://www.synology.com)
- generic `nfs`, `smb`, and `iscsi` servers
- local storage directly on nodes

# Adding the repo

Adding the repo:

```
helm repo add democratic-csi https://democratic-csi.github.io/charts/
helm repo update

if using k8s < 1.17 please use chart version 0.5.0
```

## Source Code

* <https://github.com/democratic-csi/democratic-csi>
* <https://github.com/democratic-csi/charts>
* <https://github.com/container-storage-interface/spec>
* <https://kubernetes.io/blog/2019/01/15/container-storage-interface-ga/>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| travisghansen | <a@b.c> | <https://github.com/travisghansen> |
| SecondMaintainer | <b@c.d> |  |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| controller.affinity | object | `{}` |  |
| controller.clusterDriverRegistrar.enabled | bool | `false` |  |
| controller.driver.enabled | bool | `true` |  |
| controller.driver.extraEnv | list | `[]` |  |
| controller.driver.extraVolumeMounts | list | `[]` |  |
| controller.driver.image | string | `"docker.io/democraticcsi/democratic-csi:latest"` |  |
| controller.driver.lifecycle | string | `nil` |  |
| controller.driver.logLevel | string | `"info"` |  |
| controller.driver.resources | string | `nil` |  |
| controller.driver.securityContext | string | `nil` |  |
| controller.enabled | bool | `true` | Enable Controller, taking care of Driver deployment |
| controller.externalAttacher.args[0] | string | `"--v=5"` |  |
| controller.externalAttacher.args[1] | string | `"--leader-election"` |  |
| controller.externalAttacher.args[2] | string | `"--leader-election-namespace={{ .Release.Namespace }}"` |  |
| controller.externalAttacher.args[3] | string | `"--timeout=90s"` |  |
| controller.externalAttacher.args[4] | string | `"--worker-threads=10"` |  |
| controller.externalAttacher.args[5] | string | `"--csi-address={{ .csiSocketAddress }}"` |  |
| controller.externalAttacher.enabled | bool | `false` |  |
| controller.externalAttacher.extraArgs | list | `[]` |  |
| controller.externalAttacher.image | string | `"registry.k8s.io/sig-storage/csi-attacher:v3.4.0"` |  |
| controller.externalAttacher.resources | string | `nil` |  |
| controller.externalHealthMonitorController.args[0] | string | `"--v=5"` |  |
| controller.externalHealthMonitorController.args[1] | string | `"--leader-election"` |  |
| controller.externalHealthMonitorController.args[2] | string | `"--leader-election-namespace={{ .Release.Namespace }}"` |  |
| controller.externalHealthMonitorController.args[3] | string | `"--timeout=90s"` |  |
| controller.externalHealthMonitorController.args[4] | string | `"--worker-threads=10"` |  |
| controller.externalHealthMonitorController.args[5] | string | `"--csi-address={{ .csiSocketAddress }}"` |  |
| controller.externalHealthMonitorController.enabled | bool | `false` |  |
| controller.externalHealthMonitorController.extraArgs | list | `[]` |  |
| controller.externalHealthMonitorController.image | string | `"registry.k8s.io/sig-storage/csi-external-health-monitor-controller:v0.4.0"` |  |
| controller.externalHealthMonitorController.resources | string | `nil` |  |
| controller.externalProvisioner.args[0] | string | `"--v=5"` |  |
| controller.externalProvisioner.args[1] | string | `"--leader-election"` |  |
| controller.externalProvisioner.args[2] | string | `"--leader-election-namespace={{ .Release.Namespace }}"` |  |
| controller.externalProvisioner.args[3] | string | `"--timeout=90s"` |  |
| controller.externalProvisioner.args[4] | string | `"--worker-threads=10"` |  |
| controller.externalProvisioner.args[5] | string | `"--extra-create-metadata"` |  |
| controller.externalProvisioner.args[6] | string | `"--csi-address={{ .csiSocketAddress }}"` |  |
| controller.externalProvisioner.enabled | bool | `true` |  |
| controller.externalProvisioner.extraArgs | list | `[]` |  |
| controller.externalProvisioner.image | string | `"registry.k8s.io/sig-storage/csi-provisioner:v3.1.0"` |  |
| controller.externalProvisioner.resources | string | `nil` |  |
| controller.externalResizer.args[0] | string | `"--v=5"` |  |
| controller.externalResizer.args[1] | string | `"--leader-election"` |  |
| controller.externalResizer.args[2] | string | `"--leader-election-namespace={{ .Release.Namespace }}"` |  |
| controller.externalResizer.args[3] | string | `"--timeout=90s"` |  |
| controller.externalResizer.args[4] | string | `"--workers=10"` |  |
| controller.externalResizer.args[5] | string | `"--csi-address={{ .csiSocketAddress }}"` |  |
| controller.externalResizer.enabled | bool | `true` |  |
| controller.externalResizer.extraArgs | list | `[]` |  |
| controller.externalResizer.image | string | `"registry.k8s.io/sig-storage/csi-resizer:v1.4.0"` |  |
| controller.externalResizer.resources | string | `nil` |  |
| controller.externalSnapshotter.args[0] | string | `"--v=5"` |  |
| controller.externalSnapshotter.args[1] | string | `"--leader-election"` |  |
| controller.externalSnapshotter.args[2] | string | `"--leader-election-namespace={{ .Release.Namespace }}"` |  |
| controller.externalSnapshotter.args[3] | string | `"--timeout=90s"` |  |
| controller.externalSnapshotter.args[4] | string | `"--worker-threads=10"` |  |
| controller.externalSnapshotter.args[5] | string | `"--csi-address={{ .csiSocketAddress }}"` |  |
| controller.externalSnapshotter.enabled | bool | `true` |  |
| controller.externalSnapshotter.extraArgs | list | `[]` |  |
| controller.externalSnapshotter.image | string | `"registry.k8s.io/sig-storage/csi-snapshotter:v5.0.1"` |  |
| controller.externalSnapshotter.resources | string | `nil` |  |
| controller.extraVolumes | list | `[]` |  |
| controller.hostAliases | list | `[]` |  |
| controller.hostIPC | bool | `false` |  |
| controller.hostNetwork | bool | `false` | use of host network |
| controller.livenessProbe.enabled | bool | `true` |  |
| controller.nodeSelector | object | `{}` |  |
| controller.podAnnotations | object | `{}` |  |
| controller.podLabels | object | `{}` |  |
| controller.priorityClassName | string | `""` |  |
| controller.rbac.enabled | bool | `true` | Use RBAC |
| controller.rbac.openshift | object | `{"privileged":false}` | Openshift specific RBAC changes |
| controller.replicaCount | int | `1` | Controller replicas |
| controller.strategy | string | `"deployment"` | Deployment strategy or Node sidecars with CSI daemonset |
| controller.tolerations | list | `[]` |  |
| csiDriver | object | `{"attachRequired":false,"enabled":true,"name":null,"podInfoOnMount":true,"version":"1.5.0"}` | configure csiDriver more details: https://kubernetes-csi.github.io/docs/csi-driver-object.html |
| csiDriver.enabled | bool | `true` | create the kubernetes CSIDriver |
| csiDriver.name | string | `nil` | Name of the driver should be globally unique for a given cluster |
| csiDriver.version | string | `"1.5.0"` | drive rversion |
| csiProxy.enabled | bool | `true` |  |
| csiProxy.image | string | `"docker.io/democraticcsi/csi-grpc-proxy:v0.5.3"` |  |
| csiProxy.resources | string | `nil` |  |
| driver.config | object | `{}` | Driver configuration (Truenas, ZFS Onlinux etc) - read more here |
| driver.existingConfigSecret | string | `nil` | Use existing Configuration Secret |
| enablePSP | bool | `false` |  |
| extraCaCerts | string | `""` | Add einline extra CA Certificates |
| fullnameOverride | string | `""` |  |
| nameOverride | string | `""` |  |
| node.affinity | object | `{}` |  |
| node.cleanup.image | string | `"docker.io/busybox:1.32.0"` |  |
| node.driver.enabled | bool | `true` |  |
| node.driver.extraEnv | list | `[]` |  |
| node.driver.extraVolumeMounts | list | `[]` |  |
| node.driver.image | string | `"docker.io/democraticcsi/democratic-csi:latest"` |  |
| node.driver.iscsiDirHostPath | string | `"/etc/iscsi"` |  |
| node.driver.iscsiDirHostPathType | string | `"Directory"` |  |
| node.driver.lifecycle | string | `nil` |  |
| node.driver.localtimeHostPath | string | `"/etc/localtime"` |  |
| node.driver.logLevel | string | `"info"` |  |
| node.driver.resources | string | `nil` |  |
| node.driverRegistrar.args[0] | string | `"--v=5"` |  |
| node.driverRegistrar.args[1] | string | `"--csi-address={{ .csiSocketAddress }}"` |  |
| node.driverRegistrar.args[2] | string | `"--kubelet-registration-path={{ .Values.node.kubeletHostPath }}/plugins/{{ .Values.csiDriver.name }}/csi.sock"` |  |
| node.driverRegistrar.enabled | bool | `true` |  |
| node.driverRegistrar.extraArgs | list | `[]` |  |
| node.driverRegistrar.image | string | `"registry.k8s.io/sig-storage/csi-node-driver-registrar:v2.5.1"` |  |
| node.driverRegistrar.resources | string | `nil` |  |
| node.enabled | bool | `true` |  |
| node.extraVolumes | list | `[]` |  |
| node.hostAliases | list | `[]` |  |
| node.hostIPC | bool | `true` |  |
| node.hostNetwork | bool | `true` |  |
| node.hostPID | bool | `false` |  |
| node.kubeletHostPath | string | `"/var/lib/kubelet"` |  |
| node.livenessProbe.enabled | bool | `true` |  |
| node.nodeSelector | object | `{}` |  |
| node.podAnnotations | object | `{}` |  |
| node.podLabels | object | `{}` |  |
| node.priorityClassName | string | `""` |  |
| node.rbac.enabled | bool | `true` |  |
| node.rbac.openshift.privileged | bool | `false` |  |
| node.tolerations | list | `[]` |  |
| node.windows.enabled | bool | `false` |  |
| storageClasses | list | `[]` |  |
| volumeSnapshotClasses | list | `[]` |  |
