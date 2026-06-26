# homelab-gitops

GitOps source-of-truth repo cho ArgoCD trên k3s homelab (aiserver).

ArgoCD (argocd.tungds232.com) watch repo này và tự sync manifests vào cluster.
Git = source of truth. Sửa manifest + push -> ArgoCD apply.

## Apps
- `apps/demo-hello-1` -> demo-hello-1.tungds232.com (nginx, ConfigMap HTML)
- `apps/demo-hello-2` -> demo-hello-2.tungds232.com (nginx, ConfigMap HTML)

App demo nhẹ để học GitOps (sync / rollback / drift detection).
Production apps (QLSX, cv-reviewer...) vẫn dùng pipeline push qua GitHub Actions.

## Cách hoạt động
1. Sửa file trong `apps/<name>/`
2. git commit + push
3. ArgoCD tự detect (reconcile 300s) hoặc bấm Sync trên UI
4. Rollback = git revert + push (hoặc History trên UI)
