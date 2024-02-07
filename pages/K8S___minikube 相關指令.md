category:: Kubernetes
type:: #K8s, #minikube
alias:: minikube 相關指令

- **建立 cluster**
	- `minikube start --driver=docker`
		- **參數**
		- **--driver**: `docker` | `hyperv`
		- **--mount**
	- `minikube status`
	- `minikube dashboard`
		- Integrated support for the [Kubernetes Dashboard UI](https://github.com/kubernetes/dashboard).
- **使用 minikube 指令**
	- `minikube kubectl --`
- **查看特定資源**
	- `kubectl get <資源名稱> <物件名稱>`
		- 查看實際運算節點
			- `kubectl get nodes`
		- 查看 deployments
			- `kubectl get deployments <deployment_name>`
		- 查看 services
			- `kubectl get services <service_name>`
		- 查看 default storageclass
			- `kubectl get storageclass`
		- 查看 namespace
		  id:: 65c3a5cf-c826-44b1-8f1e-efb0e57010a2
			- `kubectl get namespace`
- **檢視完整資訊**
	- `kubectl describe <資源名稱> <物件名稱>`
		- 檢視實際運算節點
			- `kubectl describe nodes <node_name>`
		- 檢視 deployment
			- `kubectl describe deployment <deployment_name>`
		- 檢視 service
			- `kubectl get service <service_name>`
- **查看所有 pods**
	- `minikube kubectl -- get po -A`
- **互動模式**
	- `minikube kubectl -- exec -it <pod_name> -- [command]`
- **部署 deployments**
	- `minikube kubectl -- create deployment <deployment_name> --image=<image>`
	- `minikube kubectl -- describe pods <deployment_name>`
- **開放 service**
	- `minikube kubectl -- expose deployment <pod_name> --port=<port>`
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
- **刪除特定資源**
	- `kubectl delete <資源名稱> <物件名稱>`
	- 刪除 pods
		- `kubectl delete pod <pod_name>`
		  id:: 658a6249-8563-433f-8f7d-e74b515a9265
		- `kubectl delete pods --all`
		  id:: 658a625c-afec-4624-8a72-7d4602d58a5f
	- 刪除 service
		- `kubectl delete service <service_name>`
		- `kubectl delete services --all`
	- 刪除 deployments
		- `kubectl delete deployment <deploymant_name>`
		- `kubectl delete deployments --all`
		  id:: 658984c2-a191-4df6-9e6d-45e6689c1283
	- 刪除所有資源
		- `minikube kubectl -- delete all --all`
- **刪除 cluster**
	- `minikube stop`
	- `minikube delete`