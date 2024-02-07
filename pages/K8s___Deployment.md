## 觀念
	- Deployment 是個更上層的抽象概念
- ## 模板 yaml
	- ```yaml
	  apiVersion: apps/v1
	  kind: Deployment
	  metadata:
	  	name: app-deployment
	  # 基本上與 ReplicaSet 的
	  spec:
	  	replicas: 3
	      selector:
	      	matchLabels:
	          	app: app-pod
	      template:
	      	matadata:
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
		- 檢視:
		- 移除: ((658984c2-a191-4df6-9e6d-45e6689c1283))