# BlackRoad-Cloud

> *Sovereign cloud. Your infrastructure, your rules.*

13 repositories. Kubernetes manifests, Cloudflare Workers, Railway deployments, and self-hosted infrastructure for BlackRoad OS.

## Infrastructure Stack
- **Cloudflare Workers** — Edge compute for all 18 products
- **Cloudflare D1** — Serverless SQLite at the edge
- **Cloudflare R2** — Object storage (S3-compatible, no egress fees)
- **Railway** — Server-side Next.js apps and APIs
- **k3s** — Lightweight Kubernetes on Pi fleet
- **Tailscale** — Secure mesh between all nodes

## Deployment
```bash
npx wrangler deploy      # Cloudflare Workers
railway up               # Railway services
kubectl apply -f k8s/    # Pi fleet
```

---
*Part of [BlackRoad OS, Inc.](https://os.blackroad.io) — Remember the Road. Pave Tomorrow.* 🖤🛣️
