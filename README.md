# GovCMS Ops - API PoC

## Local development

### Requirements

- [Tilt.dev](https://tilt.dev/)
- [Kustomize](https://kustomize.io/) (Optional)

### Useful commands

- List services inside a namespace

```bash
kubectl get svc --namespace=govcms-api
```

- Get nodes

```bash
kubectl get nodes
```

### Use the Kubernetes Dashboard UI

You can enable access to the Dashboard using the kubectl command-line tool, by running the following command:

```bash
kubectl proxy
```

Kubectl will make Dashboard available at <http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/>.

The UI can only be accessed from the machine where the command is executed.

The Dashboard UI is not deployed by default. To deploy it, run the following command:

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.5.0/aio/deploy/recommended.yaml
```

- Creating a Service Account

```bash
kubectl create serviceaccount {NAME}
```

- bind the service account to the cluster admin

```bash
kubectl create clusterrolebinding {NAME}--clusterrole=cluster-admin --serviceaccount=default:{NAME}
```

- List secrets using:

```bash
kubectl get secrets
```

- Use kubectl describe to get the access token:

```bash
kubectl describe secret {SECRET_NAME}
```