category:: Kubernetes
type:: #K8s
alias:: K8s - Persistent Volumes (PV) & Claim (PVC)

- ## Persistent Volumes (PV)
- {{embed [[K8s/Persistent Volumes]]}}
- ## Persistent Volumes Claim (PVC)
- {{embed [[K8s/Persistent Volumes Claim]]}}
- ## Pod 與 PVC連結
- > **透過 PVC，並將 PVC 當作 volume 使用**
- ```yaml
  apiVersion: apps/v1
  kind: Deployment
  # ... 與 deployment 模板相同
          spec:
              containers:
              - name: app-container
                image: uopsdod/k8s-hostname-amd64-beta:v1
                ports:
                - containerPort: 80
                volumeMounts:
                - name: app-volume
                  mountPath: /app/data
              volumes:
              - name: app-volume
                persistentVolumeClaim:
                  claimName: app-pvc
  ```
- **參數**
	- `spec.containers.volumeMounts`: 指定掛載的目錄
	- `spec.containers.volumeMounts.name`: 必須與 `volumes.name` 相同
	- `spec.containers.volumeMounts.mountPath`: container 內對應的路徑
	- `spec.volumes`
	- `spec.volumes.name`: 必須對應 `spec.containers.volumeMounts.name`
	- `spec.volumes.persistentVolumeClaim`
	- `spec.volumes.persistentVolumeClaim.claimName`: 掛載 PVC 名稱
- ## Reference
	- [K8S la8(PV & PVC)](https://hackmd.io/@S_HP7z6qQmC4l2tX34ATug/SkxaIVZQ5)