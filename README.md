# Image Lab

Static HTML/CSS image optimization test page. Origin files are copied unchanged from Downloads. `image-metadata.json` records original dimensions and byte sizes; the page presents those fixed measurements for comparison with actual HTTP responses.

## Preview

From this directory:

```sh
python3 -m http.server 8091 --directory public
```

## Deploy

The schema-v2 `hubfly.build.json` retains the project/container binding. Fetch the current Hubfly skill before platform operations:
https://hubfly.space/skills/hubfly-cli/SKILL.md

```sh
hubfly deploy --config hubfly.build.json --dockerfile Dockerfile
```

The site runs on Nginx port 80 with `/health` as its health endpoint. No JavaScript, application secrets, database, or persistent volumes are required.

## Check optimization

Open DevTools → Network → Disable cache → Img, then reload. Inspect `X-HubProxy-Image`, `Content-Type`, `Vary`, and full response body size for each asset. Repeat with device emulation and a fresh reload. CSS display dimensions alone do not change the requested source URL. No responsive source variants are generated locally, so this isolates edge image transformations.

All five images load eagerly for a consistent test set. The large PNG is approximately 7.6 MB at the origin and deliberately exercises a larger payload. Live results are in response headers, not the static source-size labels.
