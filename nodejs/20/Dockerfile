FROM        node:20-bullseye-slim

LABEL       author="Anthony" maintainer="anthonystainton+contact@gmail.com"
LABEL       org.opencontainers.image.source="https://github.com/tzRock/DockerImages"
LABEL       org.opencontainers.image.licenses="MIT"

RUN         add-apt-repository multiverse \
            && dpkg --add-architecture i386 \
            && apt-get update \
            && apt-get -y install --no-install-recommends curl ffmpeg iproute2 git sqlite3 python3 tzdata ca-certificates dnsutils build-essential steamcmd locales \
            && npm -g install npm@latest \
            && apt-get clean \
            && rm -rf /var/lib/apt/lists/* \
            && useradd -m -d /home/container container \
            && locale-gen en_US.UTF-8

ENV         LC_ALL=en_US.UTF-8
ENV         LANG=en_US.UTF-8
ENV         LANGUAGE=en_US.UTF-8

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]