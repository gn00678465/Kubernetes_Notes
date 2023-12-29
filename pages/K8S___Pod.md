category:: Kubernetes
type:: #K8s
alias:: K8s - Pod

- ## 觀念
	- > Pod 為 Kubernetes 運作的最小單位
	- 每個 Pod 都有各自識別用的 yml
	- **一個 Pod 內可以有一個或者是多個 Container**，但一般情況一個 Pod 最好只有一個 Container
	- 同一個 Pod 中的 Containers 共享相同資源及網路，彼此透過 **local port number** 溝通
- ## 模板 yaml
	- ```yaml
	  # apiVersion, kind, metadata 是必備欄位
	  apiVersion: v1
	  kind: Pod
	  metadata:
	    name: app-pod
	  spec:
	    containers:
	    - name: app-container
	      image: uopsdod/k8s-hostname-amd64-beta:v1
	      ports:
	      - containerPort: 80
	  ```
	- **minikube 指令**:
		- 建立: ((658a2340-80db-4269-a93a-5744f9df64e3))
		- 移除: ((658a6249-8563-433f-8f7d-e74b515a9265))
		- 移除所有 pods: ((658a625c-afec-4624-8a72-7d4602d58a5f))