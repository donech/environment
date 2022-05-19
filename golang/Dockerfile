FROM golang:1.18.2-alpine3.15

ENV GOPROXY https://goproxy.cn
ENV CGO_ENABLED 0
ENV GOPATH /go
ENV PATH $GOPATH/bin:$PATH

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories; \
       apk add --no-cache --virtual .deps gcc g++; \
       export GOPROXY=https://goproxy.cn; \
       go install github.com/golangci/golangci-lint/cmd/golangci-lint@v1.46.2; \
       go clean --modcache; \
       apk del --no-network .deps; \
       go version; \
       golangci-lint version
