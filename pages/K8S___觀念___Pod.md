category:: Kubernetes
type:: #K8S
alias:: 觀念 - Pod

- > Pod 為 Kubernetes 運作的最小單位
	- **一個 Pod 內可以有一個或者是多個 Container**，但一般情況一個 Pod 最好只有一個 Container
	- 同一個 Pod 中的 Containers 共享相同資源及網路，彼此透過 **local port number** 溝通