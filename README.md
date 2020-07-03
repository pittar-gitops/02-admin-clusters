# Admin Cluster Configuration

## Directories

* `base`: Common manifests and structure for each cluster.
* `cluster-nonprod`: Non-prod cluster config.
* `cluster-prod`: Production cluster config.

## Initial Environment Seeding

## Sealed Secrets

This repo is not generic (yet).  It uses Bitnami Sealed Secrets and contains sealed secrets with Quay.io credentials.  Without the TLS secret that was used to seal these secrets you can't unseal them.  For now, this demo can't be setup by anyone else because of this, but you can look around for inspiration.


**Non-prod Cluster**:
```
oc apply -k cluster-nonprod/00-argocd 
```

**Prod Cluster**:
```
oc apply -k cluster-prod/00-argocd 
```

