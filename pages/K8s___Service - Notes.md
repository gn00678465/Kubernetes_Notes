category:: Kubernetes
type:: #K8s, #Service
alias:: K8s - Service - Notes

- ## yaml 模板
	- ```yaml
	  apiVersion: v1
	  kind: Service
	  metadata:
	    name: app-service-loadbalancer
	  spec:
	    type: ClusterIP
	    selector:
	      app: app-pod
	    ports:
	    - protocol: TCP
	      port: 8080
	      targetPort: 80
	  ```
	- `spec.type`: 用來決定這個 Service 要以什麼形式建立
		- **ClusterIP** | **NodePort** | **LoadBalancer**
	- `spec.selector`: 必須對應要連線的 Pod 的 Label
	- `ports[n].protocol`: 決定連線的網路協議
		- **TCP** | **UDP**
	- `ports[n].port`:
	- `ports[n].targetPort`: 對應 Pod 的 port