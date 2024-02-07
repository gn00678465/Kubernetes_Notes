category:: Kubernetes
type:: #K8s
alias:: K8s - Namespace

- > namespace
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