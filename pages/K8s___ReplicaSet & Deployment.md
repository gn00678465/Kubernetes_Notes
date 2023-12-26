category:: Kubernetes
type:: #K8s
alias:: K8s - ReplicaSet & Deployment

- ## ReplicaSet
	- ### 觀念
		- ReplicaSet 是用來確保在 k8s 中，在資源允許的前提下，指定的 pod 的數量會跟使用者所期望的一致
		- 官方建議 ReplicaSet 要搭配 Deployment 一起使用
	- ### 模板 yaml
		- ```yaml
		  # apiVersion, kind, metadata 是必備欄位
		  apiVersion: apps/v1
		  kind: ReplicaSet
		  metadata:
		  	name: 
		  spec:
		  	# 要產生幾份副本(沒設定則預設為 1)
		  	replicas: 3
		      # 其實就是 pod template
		      template:
		      	metadata:
		          spec:
		          	containers:
		              
		  ```
		- **minikube 指令**:
- ## Deployment
	- ### 觀念
		- Deployment 是個更上層的抽象概念
- ## Reference
	- [[Kubernetes] ReplicaSet 介紹](https://godleon.github.io/blog/Kubernetes/k8s-ReplicaSet-Overview/)