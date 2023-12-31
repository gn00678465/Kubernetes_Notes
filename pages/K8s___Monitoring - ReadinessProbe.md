category:: Kubernetes
type:: #K8s, #Monitoring
alias:: K8s - Monitoring - ReadinessProbe

- > **持續**監控 Pod 的**下游服務**的健康情況
- 當下游服務不為健康的情況會將 Pod 標記為 **unready**
  logseq.order-list-type:: number
- 當下游服務回復為健康的情況會將 Pod 標記為 **ready**
  logseq.order-list-type:: number
- ## yaml
- ```yaml
  apiVersion: apps/v1
  ## 與 deployment 模板相同
          spec:
              containers:
              - name: app-container
                image: uopsdod/k8s-hostname-amd64-beta:v1
                ports:
                - containerPort: 80
                startupProbe:
                  httpGet:
                      path: /healthcheck
                      port: 80
                  initialDelaySeconds: 0
                  timeoutSeconds: 1
                  periodSeconds: 10
                  successThreshold: 1
                  failureThreshold: 30
                livenessProbe:
                  httpGet:
                      path: /healthcheck
                      port: 80
                  initialDelaySeconds: 0
                  timeoutSeconds: 1
                  periodSeconds: 1
                  successThreshold: 1
                  failureThreshold: 5
                readinessProbe:
                  httpGet:
                      path: /healthcheck_dependency
                      port: 80
                  initialDelaySeconds: 0
                  timeoutSeconds: 1
                  periodSeconds: 1
                  successThreshold: 5
                  failureThreshold: 7
  ```