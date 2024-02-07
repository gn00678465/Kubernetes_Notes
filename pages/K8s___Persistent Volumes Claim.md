category:: Kubernetes
type:: #K8s
alias:: K8s - Persistent Volumes Claim

- > PVC 是針對 PV 請求特定大小、[StorageClass](https://kubernetes.io/docs/concepts/storage/storage-classes/) 等等，PVC 是屬於 Namespace 層級的資源。
- ## yaml
- ```yaml
  apiVersion: v1
  kind: PersistentVolumeClaim
  metadata:
    name: app-pvc
  spec:
    storageClassName: sc-001
    accessModes:
    - ReadWriteMany
    resources:
      requests:
        storage: 2Gi
  ```
- **參數**
	- `spec.storageClassName`: 必須與 **PseristenVolume** 的 `spec.storageClassName` 相匹配
	- `spec.accessModes`: 與 PV 設定相同
	- `spec.resource.request.storage`: 設定 PVC 所需要的資源量
	- `spec.storageClassName`: 將 PVC 與 PV 連結所需