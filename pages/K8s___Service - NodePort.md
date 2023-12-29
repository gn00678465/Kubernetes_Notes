category:: Kubernetes
type:: #K8s, #Service
alias:: K8s - Service - NodePort

- > Worker Node 所開放的 Port 只能使用 30000 ~ 32768 的範圍內
- ## yaml
	- ```yaml
	  apiVersion: v1
	  kind: Service
	  metadata:
	    name: app-service-nodeport
	  spec:
	    type: NodePort
	    selector:
	      app: app-pod
	    ports:
	    - protocol: TCP
	      port: 8080
	      targetPort: 80
	  ```