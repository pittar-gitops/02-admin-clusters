# Admin Cluster Configuration

## Directories

* `base`: Common manifests and structure for each cluster.
* `cluster-nonprod`: Non-prod cluster config.
* `cluster-prod`: Production cluster config.

## Initial Environment Seeding

## Sealed Secrets

This repo is not generic (yet).  It uses Bitnami Sealed Secrets and contains sealed secrets with Quay.io credentials.  Without the TLS secret that was used to seal these secrets you can't unseal them.  For now, this demo can't be setup by anyone else because of this, but you can look around for inspiration.

When I instantiate this demo, the Sealed Secrets TLS secret to seed the cluster with should be in the `/envs/overlays/` directory of the environment you are launching.  The `kustomize` file is expecting a secret in that directory named `sealed-secrets-secret.yaml`.  For example, for the `nonprod` environment:
```
cp ~/backupdir/sealed-secrets-secret.yaml env/overlays/cluster-nonprod
```

This secret file is part of the repo `.gitignore`, so it will not be added to this git repo.


**Non-prod Cluster**:
```
oc apply -k envs/overlays/nonprod 
```

**Prod Cluster**:
```
oc apply -k envs/overlays/prod
```

