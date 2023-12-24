category:: Kubernetes
type:: #K8S
alias:: 觀念 - Master Node

- **結構**
	- Master Node
	- ```
	  Cluster
	     ├── Master Node
	     │  ├── API Server  <-- Worker Node
	     │  ├── Cluster Controller Manager
	     │  ├── Scheduler
	     │  ├── Cluster State Store
	     ├── Master Replicate Node
	  ```
	- Worker Node
	- ```
	  Worker Node
	  ├── Kubelet Service
	  ├── Kube Proxy Service
	  ├── Container Runtime
	  ```
- **說明**