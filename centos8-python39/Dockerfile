FROM centos:8.2.2004
ARG VERSION=3.9.0

RUN dnf clean all \
    && dnf upgrade --refresh -y\
    && dnf groupinstall 'development tools' -y \
    && dnf install bzip2-devel expat-devel gdbm-devel \
    ncurses-devel openssl-devel readline-devel \
    sqlite-devel tk-devel xz-devel zlib-devel libffi-devel wget \
    nc strace -y

RUN wget https://www.python.org/ftp/python/${VERSION}/Python-${VERSION}.tgz \
    && tar -xf Python-${VERSION}.tgz \
    && cd Python-${VERSION} && ./configure --enable-optimizations --prefix=/opt/cm_python/ && make -j $(nproc) && make altinstall \
    && rm -rf Python-${VERSION}*

RUN ln -s /opt/cm_python/bin/python3.9  /usr/local/bin/python3 \
    && ln -s /opt/cm_python/bin/pip3.9 /usr/local/bin/pip3
