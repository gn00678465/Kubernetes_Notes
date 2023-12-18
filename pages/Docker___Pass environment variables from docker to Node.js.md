category:: Note
type:: #Docker, #Node.js
alias:: Pass environment variables from docker to Node.js

- ## Passing variables to Docker
	- 使用指令將環境變數傳入 Docker container
	  logseq.order-list-type:: number
		- ```bash
		  docker run -e KEY_NAME=VALUE <container>
		  ```
	- 使用 env-file
	  logseq.order-list-type:: number
		- ```plain
		  KEY_NAME=VALUE
		  ```
		- ```bash
		  docker run --env-file <path/env-file> <container>
		  ```
- ## GET the variables in NodeJs
	- ```bash
	  # docker
	  docker rn -e Name=Madao
	  ```
	- ```js
	  // Node.js
	  console.log(process.env.Name);
	  // Madao
	  ```