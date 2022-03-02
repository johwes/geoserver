Repository for a kubernetes deployment of a geoserver and postgis instance.

Example argo application to deploy this with gitops.
"
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

"

