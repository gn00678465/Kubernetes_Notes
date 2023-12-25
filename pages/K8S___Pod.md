category:: Kubernetes
type:: #K8S
alias:: K8S - Pod

- ## 觀念
	- > Pod 為 Kubernetes 運作的最小單位
	- 每個 Pod 都有各自識別用的 yml
	- **一個 Pod 內可以有一個或者是多個 Container**，但一般情況一個 Pod 最好只有一個 Container
	- 同一個 Pod 中的 Containers 共享相同資源及網路，彼此透過 **local port number** 溝通
- ## 模板 yaml
	- ```yaml
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