category:: Kubernetes
type:: #K8s
alias:: K8s - Monitoring - Rolling Updates

- ## yaml
- ```yaml
  apiVersion: apps/v1
  kind: Deployment
  metadata:
      name: app-deployment
  spec:
      replicas: 3
      minReadySeconds: 5
      strategy:
          type: RollingUpdate
          rollingUpdate:
              maxSurge: 1
              maxUnavailable: 0
      selector:
          matchLabels:
              app: app-pod
      template:
          metadata:
              labels:
                  app: app-pod
          spec:
          ## image 相關設定
  ```
	- `spec.minReadySeconds`:
		- 容器內應用程式的啟動時間，Kubernetes 會等待設定的時間後才繼續進行升級流程
		- 如果沒有此欄位的話
			- Kubernetes 會假設該容器一開完後即可進行服務
			- 在某些極端情況下可能會造成服務無法正常運作(新誕生的 pod 尚未進入可服務階段)
	- `spec.strategy.type`:
		- 更新的策略
		- **Recreate** | **RollingUpdate**
	- `spec.strategy.rollingUpdate.maxSurge`
		- 升級過程中最多可以比原先設定所多出的 pod 數量
		- 此欄位可以為固定值或是比例(%)
	- `spec.strategy.rollingUpdate.maxUnavailable`
		- 最多可以有幾個 pod 處在無法服務的狀態
		- 與 `maxSurge` **不可同時為零** (當 `maxSurge` **不為**零時，此欄位**可**為零)
- ## 相關指令
	- 使用 **set image** 指令進行更新
		- `kubectl set image deployment <deployment> <container>=<image> --record`
	- 使用 **replace** 指令進行更新
		- `kubectl replace -f <yaml> --record`
	- 使用 **edit** 指令進行更新
		- `kubectl edit deployment <deployment> --record`
	- `--record`
		- 告知 Kubernetes **紀錄此次下達的指令**，如此一來更能清楚不同的版本(revision)間做了什麼操作
	- **查詢升級狀況**
		- `kubectl rollout status deployment <deployment>`
	- **暫停滾動升級**
		- `kubectl rollout pause deployment <deployment>`
	- **繼續滾動升級**
		- `kubectl rollout resume deployment <deployment>`
- ## Reference
	- [透過 Kubernetes Deployments 實現滾動升級](https://tachingchen.com/tw/blog/kubernetes-rolling-update-with-deployment/)