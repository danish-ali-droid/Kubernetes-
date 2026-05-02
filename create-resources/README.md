# ☸️ Kubernetes Resource Management 



This project demonstrates how to manage different Kubernetes objects using both **Imperative** and **Declarative** methods.

---

##  Pods (The Smallest Unit)
Pods are the smallest deployable units of computing that you can create and manage in Kubernetes.

### 🔹 Imperative (CLI)
```bash
kubectl run nginx-pod --image=nginx:latest
```
🔹 Declarative (YAML)
```bash
kubectl apply -f pod.yaml
```
---
##  ReplicaSets (Scaling & Self-Healing)

 A ReplicaSet ensures that a specified number of pod replicas are running at any given time.

🔹 Imperative (CLI)
 Note: Directly creating a ReplicaSet via CLI is rare; usually, we scale an existing one.
```bash
kubectl scale rs my-replicaset --replicas=3
```
🔹 Declarative (YAML)
```bash
kubectl apply -f replicaset.yaml
```
---
## Deployments (State Management)

Deployments provide declarative updates for Pods and ReplicaSets. This is the recommended way to manage your application.
🔹 Imperative (CLI)
```bash
kubectl create deployment nginx-deploy --image=nginx --replicas=5
```
🔹 Declarative (YAML)
```bash
kubectl apply -f deployment.yaml
```
---
##  Essential Management Commands

| Resource      | Get Command             | Describe Command                  |
| :-----------: | :---------------------: | :-------------------------------: |
| Pods          | kubectl get pods        | kubectl describe pod <name>       |
| Deployments   | kubectl get deploy      | kubectl describe deploy <name>    |
| ReplicaSets   | kubectl get rs          | kubectl describe rs <name>        |


##  Updates & Rollbacks

- **Change Image:**
```bash
 kubectl set image deployment/nginx-deploy nginx=nginx:1.16.1
```
- **Check History:** 
```bash
kubectl rollout history deployment/nginx-deploy
```
- **Undo Change:** 
```bash
 kubectl rollout undo deployment/nginx-deploy
 ```
---
## Note
- **Label Selectors:** Always ensure the selector in the Deployment/ReplicaSet matches the labels in the Pod template.
- **Immutability:** Some fields cannot be changed after creation; in those cases, you must delete and recreate.
- **YAML Indentation:** Kubernetes is very strict about spaces. Always use 2 spaces for nested fields.
