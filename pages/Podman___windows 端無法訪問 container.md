category:: Note
type:: #Podman, #Note
alias:: windows 端無法訪問 container

- > Podman 主要安裝到 windows 的 linux 子系統內(WSL)
- 取得 **wsl** IP Address
	- ```bash
	  # 終端機下
	  wsl
	  # 取得 wsl ip
	  ip addr
	  ```
- 使用 `netsh` 指令轉發 port
	- ```bash
	  netsh interface portproxy add v4tov4 listenport=<port-to-listen> listenaddress=0.0.0.0 connectport=<port-to-forward> connectaddress=<forward-to-this-IP-address>
	  ```