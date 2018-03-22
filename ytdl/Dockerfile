FROM lsiobase/alpine.python3.arm64

ARG BUILD_DATE
ARG VERSION
LABEL build_version="Linuxserver.io version:- ${VERSION} Build-date:- ${BUILD_DATE}"
LABEL maintainer="sparkyballs"

RUN \
echo "**** install packages ****" && \
apk add --no-cache --virtual=build-dependencies \
	g++ \
	gcc \
	make \
	python-dev && \
echo "**** install app ****" && \
wget https://yt-dl.org/downloads/latest/youtube-dl -O /usr/local/bin/youtube-dl && \
chmod a+rx /usr/local/bin/youtube-dl && \
echo "**** cleanup ****" && \
apk del --purge \
	build-dependencies && \
rm -rf /root/.cache
COPY root/ /
VOLUME /youtube
