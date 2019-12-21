#
# Dockerfile for glances
#
MAINTAINER EasyPi Software Foundation

#FROM debian:jessie
#RUN set -xe \
#    && apt-get update \
#    && apt-get -y install build-essential \
#                          curl \
#                          libfreetype6 \
#                          libfreetype6-dev \
#                          libpng12-0 \
#                          libpng12-dev \
#                          lm-sensors \
#                          pkg-config \
#                          python \
#                          python-dev \
#                          wireless-tools \
#    && curl -sSL https://bootstrap.pypa.io/get-pip.py | python \
#    && pip install "glances[action,batinfo,browser,cpuinfo,chart,docker,export,folders,gpu,ip,raid,snmp,web,wifi]" \
#    && apt-get remove -y build-essential \
#                         curl \
#                         libfreetype6-dev \
#                         libpng12-dev \
#                         pkg-config \
#                         python-dev \
#    && rm -rf /root/.cache/pip /var/lib/apt/lists/*

# Install Glances (develop branch) - ARM
FROM python:2.7-alpine
RUN apk add --no-cache --virtual .build_deps \
	gcc \
	musl-dev \
	linux-headers \
	git \
	&& git clone -b develop https://github.com/nicolargo/glances.git \
	&& pip install --no-cache-dir -r glances/requirements.txt bottle \
	&& apk del .build_deps


VOLUME /etc/glances
WORKDIR /etc/glances

EXPOSE 61208
EXPOSE 61209

CMD python -m glances $GLANCES_OPT
