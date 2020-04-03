
##############################################
#   Dockerfile to deploy base steamcmd img   #
##############################################

FROM debian:buster-slim
LABEL maintainer="me@loganhill.nz"
ARG PUID=1000

ENV STEAMDIR /home/steam/steamcmd/

RUN set -x \
        && apt-get update \
        && apt-get install -y --no-install-recommends --no-install-suggests \
		lib32stdc++6 \
		lib32gcc1 \
		curl \
		ca-certificates=20190110
RUN useradd -u $PUID -mU steam
RUN mkdir -p ${STEAMDIR}
RUN cd ${STEAMDIR}
RUN curl https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz | tar xz -C ${STEAMDIR}
RUN chown -R steam:steam /home/steam
USER steam
WORKDIR ${STEAMDIR}
VOLUME ${STEAMDIR}
