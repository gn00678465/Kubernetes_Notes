category:: Kubernetes
type:: #K8s
alias:: K8s - Namespace

- > **namespace** 其實就是實現**資源隔離**的方式，不同的 **namespaces** 的物件無法互相存取。
- {{embed ((65c3a5cf-c826-44b1-8f1e-efb0e57010a2))}}
- **預設的 namespaces**
- |--|--|
  |default|預設命名空間，創建物件、服務時，如未指定空間則就分配於此空間中。|
  |kube-node-lease||
  |kube-public|存放在裡面的物件可被所有的使用者讀取|
  |kube-system|The namespace for objects created by the Kubernetes system.|
- ## yaml
- ```yaml
  apiVersion: v1
  kind: Namespace
  metadata:
    name: app-ns
  ---
  apiVersion: apps/v1
  kind: Deployment
  metadata:
    name: beta-app-deployment
    namespace: app-ns
  // ... deployment 設定
  ---
  apiVersion: v1
  kind: Service
  metadata:
    name: beta-app-service
    namespace: app-ns
  // ... service 設定
  
  ```
- **---**: 用於分隔不同的設定檔
- 參數:
	- `metadata.namespace`: 對應的 Namespace 名稱
- ## 指令
	- `kubectl get all --namespace app-ns`
	  `kubectl get all -n app-ns`
	- **資源清理**
	- `kubectl delete ns app-ns`