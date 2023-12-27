## 觀念
	- ReplicaSet 是用來確保在 k8s 中，在資源允許的前提下，指定的 pod 的數量會跟使用者所期望的一致
	- 官方建議 ReplicaSet 要搭配 Deployment 一起使用
- ## 模板 yaml
	- ```yaml
	  # apiVersion, kind, metadata 是必備欄位
	  apiVersion: apps/v1
	  kind: ReplicaSet
	  metadata:
	      name: app-replicaset
	  spec:
	      # 要產生幾份副本(沒設定則預設為 1)
	      replicas: 3
	      # 設定 label selector，用來選擇產生副本用的 pod
	      selector:
	          matchLabels:
	              app: app-pod
	      # 其實就是 pod template
	      template:
	          metadata:
	              # .spec.template.metadata.labels 必須符合 .spec.selector 中的設定才行
	              # 否則 API server 會拒絕產生此物件
	              labels:
	                  app: app-pod
	          spec:
	              containers:
	              - name: app-container
	                image: uopsdod/k8s-hostname-amd64-beta:v1
	                ports:
	                - containerPort: 80
	  ```
	- **minikube 指令**:
		- 建立: ((658a2340-80db-4269-a93a-5744f9df64e3))
		- 檢視: `minikube kubectl -- get rs`
		- 移除: `minikube kubectl -- delete rs --all`