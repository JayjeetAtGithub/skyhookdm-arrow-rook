ARG CEPH_VERSION=v15.2.4

FROM ceph/ceph:${CEPH_VERSION}

ARG UCCROSS_ARROW_BRANCH=rados-dataset-dev

ADD docker/script.sh /

WORKDIR /

RUN dnf group install -y "Development Tools" && \
    dnf install -y cmake \
                   wget \
                   curl \
                   rados-objclass-devel \
                   python3-rados \
                   librados-devel && \
    dnf clean all && \
    git clone \
        --branch ${UCCROSS_ARROW_BRANCH} \
        --depth=1 \
        https://github.com/uccross/arrow && \
    ./script.sh && \
    rm -r /arrow
