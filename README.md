# Eclipse Data Grid — High-Perf Transport (PR candidate)

Kubernetes-safe default networking path for [eclipse-datagrid/datagrid](https://github.com/eclipse-datagrid/datagrid).

See [PR_DESCRIPTION.md](PR_DESCRIPTION.md) and apply `/home/workdir/artifacts/datagrid-develop-pr.patch` or the full tree from the companion patch on a checkout of upstream `main`.

```bash
git clone https://github.com/eclipse-datagrid/datagrid.git
cd datagrid
git checkout -b develop
git apply datagrid-develop-pr.patch
```

**Default transport:** `PortableNioTransport` (no liburing).
