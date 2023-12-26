category:: Kubernetes
type:: #K8s, #minikube
alias:: minikube 相關指令

- **建立 cluster**
	- `minikube start --driver=docker`
		- **driver**: `docker` | `hyperv`
	- `minikube status`
	- `minikube dashboard`
		- Integrated support for the [Kubernetes Dashboard UI](https://github.com/kubernetes/dashboard).
- **查看所有 pods**
	- `minikube kubectl -- get po -A`
- **查看實際運算節點**
	- `minikube kubectl -- get nodes`
	- `minikube kubectl -- describe nodes <node_name>`
- **部署 deployments**
	- `minikube kubectl -- create deployment <deployment_name> --image=<image>`
	- `minikube kubectl -- get deployments`
	- `minikube kubectl -- describe deployments <deployment_name>`
	- `minikube kubectl -- get pods`
	- `minikube kubectl -- describe pods <deployment_name>`
- **開放 service**
	- `minikube kubectl -- expose deployment <pod_name> --port=<port>`
	- `minikube kubectl -- get services`
	- `minikube kubectl -- describe <service_name>`
- **開放 cluster 連線到外部**
	- `minikube kubectl service <service_name>`
	- or
	- `minikube kubectl -- port-forward service/<service_name> <port>:<service_ port>`
- **使用模板部屬**
  id:: 658a2340-eed9-442a-9354-e07533237641
	- `minikube kubectl -- apply -f <template_yaml_file>`
	  id:: 658a2340-80db-4269-a93a-5744f9df64e3
- **關閉開放到外部的 cluster 連線**
	- `kill [kubectl_PID]`
- **刪除 service**
	- `minikube kubectl -- delete service <service_name>`
	- `minikube kubectl -- delete services --all`
- **刪除 pods**
	- `minikube kubectl -- delete pod <pod_name>`
	  id:: 658a6249-8563-433f-8f7d-e74b515a9265
	- `minikube kubectl -- delete pods --all`
	  id:: 658a625c-afec-4624-8a72-7d4602d58a5f
- **刪除 deployments**
	- `minikube kubectl -- delete deployment <deploymant_name>`
	- `minikube kubectl -- delete deployments --all`
- **刪除 cluster**
	- `minikube stop`
	- `minikube delete`