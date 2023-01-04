FROM setupphp/node:2204

ENV DEBIAN_FRONTEND=noninteractive

SHELL [ "/bin/bash", "--login", "-e", "-o", "pipefail", "-c" ]

RUN echo 'deb http://ppa.launchpad.net/apt-fast/stable/ubuntu jammy main' > \
    /etc/apt/sources.list.d/apt-fast.list \
  && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys \
    A2166B8DE8BDC3367D1901C11EE2FF37CA8DA16B \
  && apt-get update \
  && apt-get install -y --no-install-recommends nginx gettext-base acl apt-fast \
  && apt-get install -y --no-install-recommends libgtk2.0-0 libgtk-3-0 \
    libgbm-dev libnotify-dev libgconf-2-4 libnss3 libxss1 libasound2 libxtst6 xauth xvfb \
  && rm -rf /var/lib/apt/lists/*

RUN apt-get update && \
  for v in 5.6 7.0 7.1 7.2 7.3 7.4 8.0 8.1 8.2; do \
    echo php"$v"-fpm; \
  done | xargs apt-get install -y --no-install-recommends \
  && rm -rf /var/lib/apt/lists/*

LABEL org.opencontainers.image.authors="gasol.wu@gmail.com"

CMD [ "/bin/bash" ]
