# Kubernetes-safe high-performance transport for Eclipse Data Grid

## Summary
Adds a `transport` module and wires it into the cluster data path with a **Kubernetes-portable default** (no native Linux libraries required).

## Key design decision
- **Default:** `PortableNioTransport` (pure Java NIO) — runs on any K8s node
- **Opt-in only:** `NicDmaTransport` via `-Dedclipse.datagrid.transport.nicdma=true` (requires liburing; Linux-only)

## Changes
- New module `datagrid-transport` (ownership, ingest/query APIs, WAL, metrics, Vector hooks)
- `ClusterFoundation` + `HighPerfDistributorWrapper` (high-perf default ON when JAR on classpath)
- End-to-end demo: `TransportEndToEndDemo`
- Docs: `transport/CRITICAL_REVIEW.md`, `CONVERSION_STATUS.md`

## Test plan
- [x] Compile transport on JDK 21+
- [x] Run `TransportEndToEndDemo` — expect `PortableNioTransport READY (Kubernetes-safe, no native libs)` and DEMO PASSED
- [ ] CI without liburing
- [ ] Optional matrix with nicdma=true + liburing

## Note on upstream
`eclipse-datagrid/datagrid` currently has only `main` (no remote `develop`). This PR targets establishing/merging into `develop`.
