category:: Kubernetes
type:: #K8s, #Service
alias:: K8s - Service - ClusterIP

- > 預設值，代表這個 Service 只能在相同的 Cluster 內使用，無法與外部連線
- ## yaml
	- ```yaml
	  apiVersion: v1
	  kind: Service
	  metadata:
	    name: app-service-clusterip
	  spec:
	    type: ClusterIP
	    selector:
	      app: app-pod
	    ports:
	    - protocol: TCP
	      port: 8080
	      targetPort: 80
	  ```