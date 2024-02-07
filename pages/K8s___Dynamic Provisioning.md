category:: Kubernetes
type:: #K8s
alias:: K8s - Dynamic Provisioning

- > 使用預設的 storage class 作為 PV 使用，可以動態建立 PV 資源
- ## Persistent Volumes Claim (PVC)
- ```yaml
  apiVersion: v1
  kind: PersistentVolumeClaim
  metadata:
    name: app-pvc
  spec:
    storageClassName: standard
    accessModes:
    - ReadWriteMany
    resources:
      requests:
        storage: 2Gi
  ```
- 參數:
	- `spec.storageClassName`: 預設或雲端供應商提供的 storage class 名稱