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

## References

- https://stackoverflow.com/questions/65789968/microk8s-metallb-ingress
- https://toolkit.fluxcd.io/components/helm/api/
- https://microk8s.io/docs/addons#heading--list