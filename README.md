### Kubernetes Commands Cheat Sheet

#### 1. **Deploy Resources**

```bash
kubectl apply -f <filename>
```
- **Purpose**: Apply the Kubernetes resource configuration defined in the YAML file (such as deployment, service, etc.).
- Example: `kubectl apply -f frontend-deployment.yml`

#### 2. **Get Pods in a Namespace**

```bash
kubectl get pods -n <namespace>
```
- **Purpose**: Lists all pods in the specified namespace.
- Example: `kubectl get pods -n mern-app`

#### 3. **Get Services in a Namespace**

```bash
kubectl get svc -n <namespace>
```
- **Purpose**: Lists all services in the specified namespace.
- Example: `kubectl get svc -n mern-app`

#### 4. **Get Events in a Namespace**

```bash
kubectl get events -n <namespace>
```
- **Purpose**: Retrieves the events for the specified namespace to debug and check any issues.

#### 5. **Delete Resources**

```bash
kubectl delete <resource> <name> -n <namespace>
```
- **Purpose**: Deletes the specified resource (e.g., pod, deployment, service) in the given namespace.
- Example: `kubectl delete pod backend-6c579d8cc9-g7l9j -n mern-app`

#### 6. **View Logs for a Pod**

```bash
kubectl logs <pod_name> -n <namespace>
```
- **Purpose**: Shows the logs of a specific pod.
- Example: `kubectl logs backend-6b9d896588-zd4ll -n mern-app`

#### 7. **View Previous Pod Logs**

```bash
kubectl logs <pod_name> -n <namespace> --previous
```
- **Purpose**: Shows logs from the previous instance of a pod (useful for debugging restarts).

#### 8. **Describe Pod for Details**

```bash
kubectl describe pod <pod_name> -n <namespace>
```
- **Purpose**: Provides detailed information about the pod, such as events, container status, and more.

#### 9. **Exec into a Pod**

```bash
kubectl exec -it <pod_name> -n <namespace> -- <command>
```
- **Purpose**: Allows you to execute commands directly inside a pod's container.
- Example: `kubectl exec -it backend-6c579d8cc9-g7l9j -n mern-app -- bash`

#### 10. **Delete Namespace**

```bash
kubectl delete namespace <namespace_name>
```
- **Purpose**: Deletes the specified namespace and all the resources within it.
- Example: `kubectl delete namespace mern-app`

#### 11. **Get Node Information**

```bash
kubectl get nodes -o wide
```
- **Purpose**: Retrieves detailed information about the nodes in the Kubernetes cluster.

#### 12. **Delete All Resources in Namespace**

```bash
kubectl delete all --all -n <namespace>
```
- **Purpose**: Deletes all resources (pods, services, deployments) in the specified namespace.
- Example: `kubectl delete all --all -n mern-app`

---
