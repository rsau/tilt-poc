# GovCMS Ops - API PoC

## Local development

### Requirements

- [Tilt.dev](https://tilt.dev/)
- [Kustomize](https://kustomize.io/) (Optional)

### Useful commands

- List services inside a namespace

```
kubectl get svc --namespace=govcms-api
```

- Use the Kubernetes Dashboard UI

You can enable access to the Dashboard using the kubectl command-line tool, by running the following command:

```
kubectl proxy
```

Kubectl will make Dashboard available at http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/. 

The UI can only be accessed from the machine where the command is executed.

The Dashboard UI is not deployed by default. To deploy it, run the following command:

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.5.0/aio/deploy/recommended.yaml
```

Disabling the login prompt in Kubernetes Dashboard

```
kubectl patch deployment kubernetes-dashboard -n kubernetes-dashboard --type 'json' -p '[{"op": "add", "path": "/spec/template/spec/containers/0/args/-", "value": "--enable-skip-login"}]'
```
