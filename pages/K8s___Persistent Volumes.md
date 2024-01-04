category:: Kubernetes
type:: #K8s
alias:: K8s - Persistent Volumes

- > PV 是用來管理 cluster 中 storage 的資源，支援像是 NFS、Glusterfs、HostPath等多種存儲插件，擁有獨立的生命週期。
- ## yaml
- ```yaml
  apiVersion: v1
  kind: PersistentVolume
  metadata:
    name: app-pv
  spec:
    storageClassName: sc-001
    volumeMode: Filesystem
    capacity:
      storage: 2Gi
    accessModes:
      - ReadWriteMany
    hostPath:
      path: /c/Users/gn006/Downloads/k8s-demo/data
      type: DirectoryOrCreate
  ```
- **參數**
	- `spec.storageClassName`: 定義 [Storage Class](https://kubernetes.io/docs/concepts/storage/storage-classes/)名稱，讓相同 Storage Class 的 PV 與 PVC 連結
	- `spec.capacity`: 此 PV 有多少容量
	- `spec.accessModes`: PV 的掛載方式，有以下三種模式
		- **ReadWriteOnce(RWO)**: 只能被單個 node 以讀寫方式掛載
		- **ReadOnlyMany(ROX)**: 複數個 node 以只讀方式掛載
		- **ReadWriteMany(RWX)**: 複數個 node 以讀寫方式掛載
	- `spec.hostPath`:
		- **hostPath**
		- **nfs**