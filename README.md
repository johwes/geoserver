Repository for a kubernetes deployment of a geoserver and postgis instance.
The openshift/kubernetes manifests are static / not templated.. so is more of PoC / Demo quality.

Example argo application to deploy this with gitops.

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: geoserver
  namespace: openshift-gitops
spec:
  destination:
    namespace: 00-geoserver
    server: https://kubernetes.default.svc
  project: default
  source:
    path: .
    repoURL: https://github.com/johwes/geoserver.git
    targetRevision: HEAD
  syncPolicy:
    syncOptions:
    - CreateNamespace=true


```
