# Flux config branch

```bash
flux bootstrap github --owner arthurbdiniz --repository flux-poc --branch flux --path=clusters/microk8s --personal true
```

```bash
flux create source git deploy \
    --url https://github.com/arthurbdiniz/flux-poc \
    --branch deploy \
    --interval 30s \
    --export | tee -a clusters/microk8s/deploy.yaml
```

```bash
flux create kustomization staging \
    --source deploy \
    --path "./staging" \
    --prune true \
    --validation client \
    --interval 10m \
    --export | tee -a clusters/microk8s/staging.yaml
```

```bash
flux create kustomization production \
    --source deploy \
    --path "./production" \
    --prune true \
    --validation client \
    --interval 10m \
    --export | tee -a clusters/microk8s/production.yaml
```

```bash
watch flux get sources git
```