# Deployment status

- Project: `test` (`prj_def1e988-c401-47e4-8d6b-52a322096581`)
- Region: `usa-central` / `us-3`
- Intended container: `image-lab`
- Reconciliation mode: smart (default)
- Shared tier: 0.3 vCPU, 256 MiB RAM, 1 GiB disk, auto-sleep
- Build: `build_888e1740-8265-4ca9-a0ad-458021ffcb5d`
- Final Dashboard state: `failed`, `CLI_UPLOAD_FAILED`

The Docker image built successfully. Upload failed before transferring any bytes: the assigned US3 registry at `198.58.118.160:10017` timed out; the HTTP fallback reported no route to host. Independent checks confirmed ports 80 and 443 reachable and port 10017 timing out. No container was created. Public ingress and live optimization remain unverified.

Local browser checks passed at mobile (390 px) and desktop (1280 px) sizes: all five images decoded, no horizontal overflow, and zero scripts. Original measurements are in `image-metadata.json`.

Restore registry connectivity before retrying; preserve the project binding in `hubfly.build.json`. Fetch the live Hubfly skill before deployment work.

## Retry from standalone project

Build `build_d540774b-6e72-4d24-976d-ddcead9c015e` was run from `/home/octave/Desktop/image-lab` against project `test`, US3, with smart mode. Local build succeeded; upload transferred zero bytes and failed because both HTTPS and HTTP connections to `198.58.118.160:10017` reported no route to host. The site remains unpublished.
