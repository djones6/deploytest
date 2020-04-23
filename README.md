# deploytest
Test Kustomize acting on a 'vanilla' Kubernetes Deployment to add or modify environment variables.

### What to do
Print the original deployment with just 'base' modifications (namespace):
```
kubectl kustomize ./base/
```

Print the deployment with a number of patches applied to extend the environment variables section (`spec/template/spec/containers/env`):
```
kubectl kustomize ./overlay/
```

### What it does
There is a base deployment in `base/deploy.yaml` which contains two environment variables: `FOO` and `BAT`.

There are three patches:
- patch1.yaml adds two new environment variables (`APPLE` and `BANANA`).
- patch2.yaml adds two more environment variables (`PEAR` and `PLUM`).
- patch3.yaml modifies one of the initial env vars (`FOO`) to have a new value.

The result is a deployment that contains all six env vars, one of which has been updated with a new value.
