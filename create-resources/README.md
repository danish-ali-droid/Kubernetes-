# Kubernetes Resource Examples

This directory contains example Kubernetes manifests for creating basic resources using `nginx` containers.

## Files

- `deployment.yaml`
  - Defines an `apps/v1` Deployment named `nginx-deployment`.
  - Deploys 5 replicas of an `nginx` container.
  - Uses labels `env: practice` and `type: frontend`.

- `pod.yaml`
  - Defines a single `v1` Pod named `nginx-pod`.
  - Runs one `nginx` container.
  - Uses labels `env: demo` and `type: frontend`.

- `rc.yaml`
  - Defines a `v1` ReplicationController named `nginx-rc`.
  - Deploys 3 replicas of an `nginx` Pod template.
  - Uses labels `env: demo` and `type: frontend`.

- `replicset.yaml`
  - Defines an `apps/v1` ReplicaSet named `nginx-rs`.
  - Deploys 5 replicas of an `nginx` Pod template.
  - Uses label `env: practice`.

## Usage

Apply any manifest using `kubectl`:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f pod.yaml
kubectl apply -f rc.yaml
kubectl apply -f replicaset.yaml
```

Delete resources when finished:

```bash
kubectl delete -f deployment.yaml
kubectl delete -f pod.yaml
kubectl delete -f rc.yaml
kubectl delete -f replicaset.yaml
```

## Notes

- The manifests are simple examples for learning resource creation.
- The `deployment.yaml` and `replicaset.yaml` use `apps/v1` API.
- The `pod.yaml` and `rc.yaml` use `v1` API.
