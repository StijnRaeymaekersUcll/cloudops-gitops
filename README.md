# cloudops-gitops

GitOps repo for my school cluster, managed by Argo CD (app-of-apps pattern).

```
root.yaml            # root Application, points at apps/
apps/                # one Argo CD Application per app
  hello.yaml
manifests/           # plain Kubernetes manifests per app
  hello/
```

## Bootstrap (once)

```bash
kubectl apply -f root.yaml
```

After that, every change pushed to `main` is synced automatically.

## Add a new app

1. Put its manifests in `manifests/<app>/`
2. Copy `apps/hello.yaml` to `apps/<app>.yaml`, change `name`, `path` and `destination.namespace`
3. Commit + push
