Related Github issue: https://github.com/helmfile/helmfile/issues/743

When using a kustomization, `helmfile template` fails with `Error: unknown flag: --load_restrictor]`
Downgrading `kustomize` to i.e. `4.5.6` fixed it.

Steps to reproduce:

* Install Kustomize >= 5

Then:

    https://github.com/hinricht/helmfile-kustomize5.git
    cd helmfile-kustomize5
    helmfile template

With Kustomize>=5 this error will show:

```
$ helmfile template
in ./helmfile.yaml: [exit status 1

COMMAND:
  kustomize -o /tmp/chartify559297089/test/monitoring/test/templates/kustomized.yaml build --load_restrictor=none --enable_alpha_plugins /tmp/chartify559297089/test/monitoring/test

OUTPUT:
  Error: unknown flag: --load_restrictor]
```

With Kustomize <5 `helmfile template` works as expected.
