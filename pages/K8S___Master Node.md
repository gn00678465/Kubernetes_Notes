category:: Kubernetes
type:: #K8s
alias:: K8s - Master Node

- ## 結構
	- **Master Node**
	- ```
	  Cluster
	     ├── Master Node
	     │  ├── API Server  <-- Worker Node
	     │  ├── Cluster Controller Manager
	     │  ├── Scheduler
	     │  ├── Cluster State Store
	     ├── Master Replicate Node
	  ```
	- **Worker Node** (**Slave Node**)
	- ```
	  Worker Node
	  ├── Kubelet Service
	  ├── Kube Proxy Service
	  ├── Container Runtime
	  ```
- ### 說明
	- **Cluster**:
	- **Master Node**: 控制、支配整個 cluster 的運作
		- **API Server**:
		- **Cluster Controller Manger**:
		- **Scheduler**:
		- **Cluster State Store**:
	- **Worker Node**: 又稱 **Slave Node**，受 master node 支配的 node，負責運行 pod
		- **Kubelet Service**:
		- **Kube Proxy Service**:
		- **Container Runtime**:
- ## Reference
	- [認識 kubernetes-2](https://ithelp.ithome.com.tw/articles/10297250)