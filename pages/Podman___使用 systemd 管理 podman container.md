category:: Note
type:: #Podman, #Note
alias:: 使用 systemd 管理 podman container

- > podman 並不像 docker 有 Docker Engine (a.k.a. dockerd)，重開機後並不會自動重啟(**--restart=always** 也不會)
- [將 container 轉成 systemd service file](https://docs.podman.io/en/latest/markdown/podman-generate-systemd.1.html)
- ```bash
  podman generate systemd --new --files --name <systemd_name>
  ```
- 建立並複製 systemd service file
	- **rootless container**
		- > 假設沒有資料夾需要新增
		- ```bash
		  mkdir -p ~/.config/systemd/user
		  ```
		- **copy**
		- ```bash
		  cp -Z <systemd_name>.service ~/.config/systemd/user
		  ```
	- **root container**
		- ```bash
		  sudo cp -Z <systemd_name>.service /etc/systemd/system
		  ```
- 啟用
	- **rootless container**
		- ```bash
		  systemctl --user enable <systemd_name>.service
		  systemctl --user start <systemd_name>.service
		  systemctl --user status <systemd_name>.service
		  ```
	- **root container**
		- ```bash
		  sudo systemctl --user enable <systemd_name>.service
		  sudo systemctl --user start <systemd_name>.service
		  sudo systemctl --user status <systemd_name>.service
		  ```
- 可透過 `pstree` 來看 **systemd** 與 **podman** 的 container 的互動
- ## Reference
	- [WSL2 中使用 systemd 管理 podman 的 container](https://www.omegaatt.com/blogs/develop/2023/wsl2_systemd_podman.html)