category:: Kubernetes
type:: #K8s, #Service
alias:: K8s - Service - LoadBalancer

- > 必須搭配從雲端服務商或本地端啟動的 LoadBalancer 服務
- ## yaml
	- ```yaml
	  apiVersion: v1
	  kind: Service
	  metadata:
	    name: app-service-loadbalancer
	  spec:
	    type: LoadBalancer
	    selector:
	      app: app-pod
	    ports:
	    - protocol: TCP
	      port: 8080
	      targetPort: 80
	  ```
	- **minikube 指令**:
		- 啟動模擬 LoadBalancer 服務: `minikube tunnel`