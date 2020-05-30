FROM  centos:7.6.1810
MAINTAINER John van Zantvoort <john@vanzantvoort.org>

RUN groupadd --gid 1000 docker && \
    adduser -u 1000 -g docker --home /home/docker --shell /bin/sh docker && \
    chmod 755 /home/docker && \
    echo '%_topdir /home/docker/rpmbuild' > /.rpmmacros


RUN USER=docker && \
    GROUP=docker && \
    curl -SsL https://github.com/boxboat/fixuid/releases/download/v0.4/fixuid-0.4-linux-amd64.tar.gz | tar -C /usr/local/bin -xzf - && \
    chown root:root /usr/local/bin/fixuid && \
    chmod 4755 /usr/local/bin/fixuid && \
    mkdir -p /etc/fixuid && \
    printf "user: $USER\ngroup: $GROUP\n" > /etc/fixuid/config.yml

RUN yum -y install epel-release && \
    yum -y install mock rpm-build rpmdevtools sudo tito && \
    yum clean all && \
    echo "docker ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/docker

WORKDIR /home/docker

USER docker:docker

CMD ["/bin/bash"]
