# CAPI Node Images

Kubernetes node images for [Cluster API](https://cluster-api.sigs.k8s.io/), built with [image-builder](https://github.com/kubernetes-sigs/image-builder) via GitHub Actions and published as OCI images on Docker Hub.

## Images

| OS | Image |
|----|-------|
| Flatcar (stable) | `floatingcontainers/flatcar-<version>` |
| Ubuntu 26.04 | `floatingcontainers/ubuntu-2604-<version>` |

Current Kubernetes version: **1.36.4**

Browse all tags on [Docker Hub](https://hub.docker.com/u/floatingcontainers) or the [Releases](../../releases) page.

## Usage

Each image is a `scratch` image containing a single disk at `/disk/image.qcow2`. It is not runnable; use it as a disk source (e.g. KubeVirt containerDisk) or extract the qcow2:

```bash
id=$(docker create floatingcontainers/<image>:<tag> /bin/true)
docker cp "$id":/disk/image.qcow2 ./image.qcow2
docker rm "$id"
```

## Building

Images are built manually via the **Build CAPI OCI Image** workflow (Actions → Run workflow).
