# Deployment desire state branch


#### Staging release

```bash
flux create helmrelease stagin --source GitRepository/deploy --values=stagin-values.yaml --chart "helm" --target-namespace staging --interval 30s --export
```

#### Production release

```bash
flux create helmrelease production --source GitRepository/deploy --values=production-values.yaml --chart "helm" --target-namespace production --interval 30s --export
```


```bash
flux get helmreleases
```