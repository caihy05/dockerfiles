FROM alpine:3.9

ENV ETCD_VER=v3.4.3 \
    DOCKER_VER=19.03.5 \
    CONTAINERD_VER=1.2.6 \
    CNI_VER=v0.7.5 \
    HELM_VER=v2.14.1 \
    DOCKER_COMPOSE_VER=1.22.0 \
    CALICOCTL_VER=v3.4.4 \
    EXT_BIN_VER=0.4.0
     
RUN mkdir -p /extra && \
    \
    wget https://github.com/etcd-io/etcd/releases/download/$ETCD_VER/etcd-$ETCD_VER-linux-arm64.tar.gz && \
    tar zxf etcd-$ETCD_VER-linux-arm64.tar.gz && \
    cd etcd-$ETCD_VER-linux-arm64 && \
    mv etcd etcdctl /extra && \
    cd / && rm -rf etcd-$ETCD_VER-linux-arm64* && \
    \
    wget https://download.docker.com/linux/static/stable/aarch64/docker-$DOCKER_VER.tgz && \
    tar zxf docker-$DOCKER_VER.tgz && \
    mv docker/* /extra && \
    rm -rf docker* && \
    \
    wget https://pkg.cfssl.org/R1.2/cfssl_linux-arm && \
    wget https://pkg.cfssl.org/R1.2/cfssljson_linux-arm && \
    wget https://pkg.cfssl.org/R1.2/cfssl-certinfo_linux-arm && \
    mv cfssl_linux-arm /extra/cfssl && \
    mv cfssljson_linux-arm /extra/cfssljson && \
    mv cfssl-certinfo_linux-arm /extra/cfssl-certinfo && \
    \
    wget https://github.com/containernetworking/plugins/releases/download/$CNI_VER/cni-plugins-arm64-$CNI_VER.tgz && \
    mkdir /cni && tar zxf cni-plugins-arm64-$CNI_VER.tgz -C /cni && \
    cd /cni && mv bridge flannel host-local loopback portmap tuning /extra && \
    cd / && rm -rf cni* && \
    \
    wget https://get.helm.sh/helm-$HELM_VER-linux-arm64.tar.gz && \
    tar zxf helm-$HELM_VER-linux-arm64.tar.gz && \
    mv linux-arm64/helm /extra && \
    rm -rf linux-arm64 helm-$HELM_VER-linux-arm64.tar.gz && \
#    \
#    wget https://storage.googleapis.com/cri-containerd-release/cri-containerd-$CONTAINERD_VER.linux-arm64.tar.gz && \
#    mkdir cri-containerd /extra/containerd-bin && \
#    tar zxf cri-containerd-$CONTAINERD_VER.linux-amd64.tar.gz -C cri-containerd && \
#    cd cri-containerd/usr/local/bin && mv containerd containerd-shim containerd-shim-runc-v1 crictl ctr /extra/containerd-bin && \
#    mv ../sbin/runc /extra/containerd-bin && \
#    cd / && rm -rf cri-containerd* && \
    \
    wget https://github.com/ubiquiti/docker-compose-aarch64/releases/download/$DOCKER_COMPOSE_VER/docker-compose-Linux-aarch64 && \
    mv docker-compose-Linux-aarch64 /extra/docker-compose && \
    \
    wget https://github.com/projectcalico/calicoctl/releases/download/$CALICOCTL_VER/calicoctl-linux-arm64 && \
    mv calicoctl-linux-arm64 /extra/calicoctl

CMD [ "sleep", "360000000" ]