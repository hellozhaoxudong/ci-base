# nodejs 16.14.2 | npm | yarn | 
# git | docker-cli | kubectl 1.23.0 | rancher-cli v2.6.4 |
FROM alpine:3.15.3

RUN mkdir -p /data
WORKDIR /data

# 安装openjdk8、git、nodejs、npm、docker-cli
RUN sed -i "s/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g" /etc/apk/repositories && \
    apk update && \
    apk add --no-cache \
	git nodejs=16.14.2-r0 npm docker-cli

# 安装yarn
RUN npm config set registry https://registry.npmmirror.com && \
    npm install --global yarn

# 安装kubectl
RUN wget https://dl.k8s.io/release/v1.23.0/bin/linux/amd64/kubectl && \
    mv kubectl /usr/local && \
    chmod +x /usr/local/kubectl
ENV PATH=$PATH:/usr/local

# 安装rancher-cli
RUN wget http://rancher-mirror.cnrancher.com/cli/v2.6.4/rancher-linux-amd64-v2.6.4.tar.gz && \
    tar -zxf rancher-linux-amd64-v2.6.4.tar.gz -C /usr/local && \
    rm -f rancher-linux-amd64-v2.6.4.tar.gz
ENV PATH=$PATH:/usr/local/rancher-v2.6.4