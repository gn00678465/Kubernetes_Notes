category:: Kubernetes
type:: #K8s, #Monitoring
alias:: K8s - Monitoring - StartupProbe, LivenessProbe

- > **LivenessProbe**: 在 Pod 啟動時確認 Pod 自身的健康情況
  **LivenessProbe**: **持續**監控 Pod 自身的健康情況
- ## yaml 模板
- ```yaml
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
  ```
- **initialDelaySeconds**
- **timeoutSeconds**
- **periodSeconds**
- **successThreshold**
- **failureThreshold**