category:: Environment
type:: #Docker
alias:: Docker 與 Podman 的差異點

- ## 架構圖
	- ![docker_v_s_podman.webp](../assets/docker_v_s_podman_1703464016863_0.webp)
- ## 差異點
	- 沒有 daemon, 預防單點故障(SPOF,Single Point of Failure)
		- Podman 並不是透過 daemon 服務的方式去跟 kernel 溝通。
		- Docker 則由 Docker daemon 負責控制所有 child process，當 Docker daemon 故障，底下的 child process(容器)，會全部故障。
	- 不需要 Root User 使用權限也可以運行容器
		- podman 在創建 container 時可以自由使用不同 `uid` & `gid` 去管理這個 container process。
		- Docker 使用 Daemon 去建立 container process(非 `root` 在 `linux` 建立檔案等使用上會有限制)
	- podman 可以跑 pods
- ## Reference
	- [在 Laptop 環境使用 Podman （含 Windows & MacOS）](https://www.osarea.com/%E5%9C%A8-laptop-%E7%92%B0%E5%A2%83%E4%BD%BF%E7%94%A8-podman-%EF%BC%88%E5%90%AB-windows-macos%EF%BC%89)