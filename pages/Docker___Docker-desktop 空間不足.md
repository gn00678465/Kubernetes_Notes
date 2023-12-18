category:: Environment
type:: #Docker
alias:: Docker-desktop 空間不足

- shutdown docker-desktop
- shutdown wsl: `wsl --shutdown`
- dump docker-desktop-data
	- `wsl --export docker-desktop-data D:\u2004.tar`
- unregister docker-desktop-data
	- `wsl --unregister docker-desktop-data`
- import docker-desktop-data to specific folder
	- `wsl --import docker-desktop-data "D:\Program Files\wsl-docker-data" D:\docker-desktop-data.tar --version 2`