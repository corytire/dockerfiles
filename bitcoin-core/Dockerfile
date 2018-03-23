FROM ubuntu:latest

ARG BUILD_DATE
ARG VERSION
LABEL build_version="Build-version:- ${VERSION} Build-date:- ${BUILD_DATE}"
LABEL maintainer="corytire"

RUN \
add-apt-repository ppa:bitcoin/bitcoin && \
apt-get update && \
apt-get install -y \
	bitcoin-qt
apt-get clean && \
rm -rf \
	/tmp/* \
	/var/lib/apt/lists/* \
	/var/tmp/*

RUN \
export uid=1000 gid=1000 && \
    mkdir -p /home/developer && \
    echo "developer:x:${uid}:${gid}:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:${uid}:" >> /etc/group && \
    echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer && \
    chown ${uid}:${gid} -R /home/developer

USER developer
ENV HOME /home/developer
VOLUME /bitcoin /config
CMD /usr/local/bin/bitcoin-qt
