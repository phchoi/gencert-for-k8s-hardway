FROM ubuntu:18.04
LABEL maintainer="philip@grassbag.net"
ENV DEBIAN_FRONTEND noninteractive \
    GOROOT /usr/local/go \
    GOPATH /root/go
RUN apt-get update && \
    apt-get install -y curl wget build-essential git && \
    curl -o /usr/local/bin/kubectl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl && \
    chmod +x /usr/local/bin/kubectl && \
    wget -O /tmp/go.tar.gz --https-only https://dl.google.com/go/go1.13.1.linux-amd64.tar.gz && \
    tar -C /usr/local -zxvf /tmp/go.tar.gz && \
    echo "export GOROOT=/usr/local/go" >> /root/.bashrc && \
    echo "export GOPATH=/root/go" >> /root/.bashrc && \
    echo "export PATH=$PATH:/usr/local/go/bin:/root/go/bin" >> /root/.bashrc && \
    /usr/local/go/bin/go get -v -u github.com/cloudflare/cfssl/cmd/cfssl && \
    /usr/local/go/bin/go get -v -u github.com/cloudflare/cfssl/cmd/cfssljson
