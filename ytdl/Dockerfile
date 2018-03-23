FROM lsiobase/alpine.python:3.7

ARG BUILD_DATE
ARG VERSION
LABEL build_version="Build-version:- ${VERSION} Build-date:- ${BUILD_DATE}"
LABEL maintainer="corytire"

RUN \
apk add --no-cache --virtual=build-dependencies \
	g++ \
	gcc \
	make \
	ffmpeg \
	atomicparsley \
	python-dev && \
pip install --no-cache-dir -U \
	pycryptodomex \
	youtube-dl && \
apk del --purge \
	build-dependencies && \
rm -rf \
	/root/.cache
VOLUME /youtube /config
