FROM        node:18-bookworm

LABEL       author="Anthony" maintainer="anthonystainton+contact@gmail.com"
LABEL       org.opencontainers.image.source="https://github.com/ItzRock/DockerImages/"
LABEL       org.opencontainers.image.licenses="MIT"

RUN         apt-get update \
            && apt-get -y install --no-install-recommends musl ffmpeg iproute2 git sqlite3 python3 tzdata ca-certificates dnsutils build-essential locales \
            && npm -g install npm@latest \
            && apt-get clean \
            && rm -rf /var/lib/apt/lists/* \
            && useradd -m -d /home/container container \
            && locale-gen en_US.UTF-8
RUN ln -s /lib/libc.musl-x86_64.so.1 /lib/ld-linux-x86-64.so.2
ENV         LC_ALL=en_US.UTF-8
ENV         LANG=en_US.UTF-8
ENV         LANGUAGE=en_US.UTF-8

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]