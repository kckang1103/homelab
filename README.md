# homelab

GitOps config for a three-node kubeadm cluster on Raspberry Pi 5s, deployed by Argo CD.
The build is written up starting at https://www.kichulkang.com/blog/raspberry-pi-kubernetes-part-1/.

| Path | What |
| --- | --- |
| `bootstrap/root.yaml` | The only Application applied by hand; it deploys everything in `apps/` |
| `apps/` | One Argo CD Application per component |
| `argocd/` | Argo CD itself (v3.5.6), without Dex and notifications |
| `etcd-backup/` | CronJob taking an etcd snapshot every 6 hours |

Bootstrap on a fresh cluster:

```sh
kubectl apply -k argocd/ --server-side
kubectl apply -f bootstrap/root.yaml
```

This repo is public, so no secrets go in it.
