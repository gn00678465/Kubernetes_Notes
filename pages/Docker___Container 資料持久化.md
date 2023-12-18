category:: Environment
type:: #Docker
alias:: Docker container 資料持久化

- ## 概述
- Docker 將資料儲存於 container 外的方法
	- ![volumes on the Docker host](https://docs.docker.com/storage/images/types-of-mounts-volume.png)
	- Bind Mount: 資料存在 Filesystem 中。
	- Volume: 資料存在 Filesystem 內的 Docker Area 中。
	- Tmpfs Mount: 資料存放在記憶體中。
- 查看 Container 綁定的 Volume 或 Bind Mount 狀態
	- 使用 `docker inspect` 會有一個 Mount 的區塊，描述了資料綁定的細節。
- ## --mount 與 -v/ --volume
	- 建立 docker container 皆可以使用 `--mount` 或 `-v` 來綁定資料。
	- ```bash
	  -v, --volume list      Bind mount a volume
	      --mount mount      Attach a filesystem mount to the container
	  ```
- ## Volume
	- > Docker 用來存放持久化資料的空間。
	- ### 建立 Volume
		- ```bash
		  docker volume create [OPTIONS] [VOLUME]
		  
		  -d, --driver string   Specify volume driver name (default "local")
		      --label list      Set metadata for a volume
		  -o, --opt map         Set driver specific options (default map[])
		  ```
	- ### 綁定 Volume
		- ```bash
		  # -v
		  docker run -d -v [VOLUME]:[target]
		  
		  # -mount
		  docker run -d --mount source=[VOLUME],target=[target]
		  ```
		- **[target]**，代表 Container 內的路徑，也就是將 Container 內的路徑掛載到 **[VOLUME]**
	- ### 移除 Volume
		- ```bash
		  docker volume rm [OPTIONS] VOLUME [VOLUME...]
		  ```
- ## Bind Mount
	- > 將資料存放到 **Filesystem**
	- ### 綁定 Filesystem
		- ```bash
		  # -v
		  docker run -d -v [source]:[target]
		  
		  # --mount
		  docker run -d --mount type=bind,source=[source],target=[target]
		  ```
		- 使用 `--mount` ，必須設定綁定的形式 `type=bind`。
		- `type` 可以為 `bind`、 `volume`、`tmpfs`，預設為 `volume`。
- ## Tmpfs Mount
	- > Tmpfs，全名 Temporary File System，是在 Linux 暫存檔儲存空間的常見名稱，通常以掛載檔案系統方式實現。  
	  使用 Tmpfs Mount 則資料會存在於記憶體上，在重啟 Container 的時候就會 Reset 資料。
	- ### 綁定 Memory Disk
		- 使用 Tmpfs Mount 並不是使用 `-v` 的選項，而是使用 `--tmpfs` ，`--tmpfs` 就如同 `-v`一樣簡化了使用 `--mount` 時所需的設定。
		- ```bash
		  # --tmpfs
		  docker run -d --tmpfs [target]
		  
		  # --mount
		  docker run -d --mount type=tmpfs,[target]
		  ```
- ## Reference
- [Docker筆記 - 讓資料遠離Container，使用 Volume、Bind Mount 與 Tmpfs Mount](https://medium.com/alberthg-docker-notes/docker%E7%AD%86%E8%A8%98-%E8%AE%93%E8%B3%87%E6%96%99%E9%81%A0%E9%9B%A2container-%E4%BD%BF%E7%94%A8-volume-bind-mount-%E8%88%87-tmpfs-mount-6908da341d11)