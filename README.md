# homelab-gitops

GitOps source-of-truth repo cho ArgoCD trên k3s homelab (aiserver).

ArgoCD (argocd.tungds232.com) watch repo này và tự sync manifests vào cluster.
Git = source of truth. Sửa manifest + push -> ArgoCD apply.

## Apps
Hiện chưa có app nào. 2 app demo (`demo-hello-1`, `demo-hello-2`) đã gỡ ngày 2026-11-16
(ArgoCD Application đã xoá; xem lại trong git history nếu cần).
Production apps (QLSX, cv-reviewer...) vẫn dùng pipeline push qua GitHub Actions.

## Cách hoạt động
1. Sửa file trong `apps/<name>/`
2. git commit + push
3. ArgoCD tự detect (reconcile 300s) hoặc bấm Sync trên UI
4. Rollback = git revert + push (hoặc History trên UI)
