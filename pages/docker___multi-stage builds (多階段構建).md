category:: Environment
type:: #Docker
alias:: multi-stage builds (多階段構建)

- > 製作容器映像檔時有個常見的原則: 映像檔越小越好
- ## Example
  collapsed:: true
	- golang
	- ```Dockerfile
	  FROM alpine AS base
	  RUN apk add --no-cache curl wget
	  
	  FROM golang:1.9.2 AS go-builder
	  WORKDIR /go
	  COPY *.go /go/
	  RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o main .
	  
	  FROM base
	  COPY --from=go-builder /go/main /main
	  CMD ["/main"]
	  ```
	- node.js
	- ```dockerfile
	  FROM node:latest as build-stage
	  
	  ENV WORKDIR=/app
	  WORKDIR $WORKDIR
	  COPY . $WORKDIR
	  
	  RUN npm install
	  RUN npm run build
	  
	  FROM nginx:alpine as production-stage
	  
	  RUN mkdir /app
	  
	  COPY --from=build-stage /app/dist /app
	  COPY --from=build-stage [nginx.conf] /etc/nginx/nginx.conf
	  
	  EXPOSE 443
	  EXPOSE 80
	  ```
	- *[nginx.conf]* 取代為放置 nginx.conf 的路徑
- ## Stages
  collapsed:: true
	- ### Stage 0 (base)
		- ```dockerfile
		  FROM alpine AS base
		  RUN apk add --no-cache curl wget
		  ```
		- 使用 `AS <NAME>` 將 **Stage 0** 命名為 `base`
		- 以 `alpine` 為 parent image 建立中間映像檔，並在裡面安裝所需的套件 (curl, wget)
	- ### Stage 1 (builder)
		- ```dockerfile
		  FROM golang:1.9.2 AS go-builder
		  WORKDIR /go
		  COPY *.go /go/
		  RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o main .
		  ```
		- 將 **Stage 1** 命名為 `go-builder`
		- 編譯 packages & dependencies
	- ### Stage 2
		- ```dockerfile
		  FROM base
		  COPY --from=go-builder /go/main /main
		  CMD ["/main"]
		  ```
		- 利用 **stage 0** (stage base) 建立好的中間映像檔作為 parent image
		- 利用 `COPY` 取得剛剛在 stage 1 (stage go-builder) 產生的 artifacts
			- `COPY --from=1`
			- `COPY --from=<intermediate_image_name>`
			- 實際行為是從該 image 把對應路徑的檔案或 artifacts，複製進 container
	- ### 小技巧
		- `FROM <base_image> as <stage_name>`
			- 記得為每個 stage 命名，提高整體可讀性
			- 未來若有更多 stage 加入時，可以不需跟著修改現存的 `COPY` 指令
		- `COPY --from=<stage_name>`
			- 多利用 stage 名字取代數字以提高可讀性及維護性
- ## Reference
- [透過 Multi-Stage Builds 改善持續交付流程](https://tachingchen.com/tw/blog/docker-multi-stage-builds/)
- [Multi-stage Build](https://ithelp.ithome.com.tw/articles/10247981)