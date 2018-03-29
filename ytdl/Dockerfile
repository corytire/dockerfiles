FROM alpine:latest
MAINTAINER corytire

RUN \
apk update && \
apk add --no-cache\
	python3 -m ensurepip\
	ffmpeg && \
rm -r /usr/lib/python*/ensurepip && \
pip3 install --upgrade pip setuptools youtube-dl&& \
rm -r /root/.cache
WORKDIR /youtube
ENTRYPOINT ["youtube-dl"]
VOLUME /youtube /config
