category:: Environment
  type:: #Docker, #Docker-compose
  alias:: Compose file - ports

- ### Short syntax
	- > `HOST:CONTAINER`
	- ```yaml
	  version: '3'
	  services:
	  	service-name:
	      	....
	          ports:
	          	- "80"
	              - "443:443/tcp"
	              - "3000-3005:3000-3005"
	  ```
- ### Long syntax
	- version:: 3.2+
	- ```yaml
	  version: '3'
	  services:
	  	service-name:
	      	....
	          ports:
	          	- target: 80
	                published: 80
	                protocol: tcp
	                mode: host
	              - target: 443
	                published: 443
	                protocol: tcp
	                mode: host
	  ```
	- `target`: container 內的 port
	- `published`: 對外的 port
	- `protocol`: `tcp` or `udp`
	- `mode`:
		- `host`: for publishing a host port on each node
		- `ingress`: for a swarm mode port to be load balanced
- ## Reference
	- [ports](https://docs.docker.com/compose/compose-file/compose-file-v3/#ports)