FROM rhasspy/rhasspy:2.5.11
LABEL maintainer="Michael Hansen <mike@rhasspy.org>"

ENV LANG C.UTF-8

RUN mkdir -p /var/cache/apt/arm64/archives/partial

RUN apt-get autoclean

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
      git \
      alsa-utils \
      dkms \
      i2c-tools \
      libasound2-plugins

RUN git clone "https://github.com/respeaker/seeed-voicecard" \
    && cd seeed-voicecard \
    && chmod a+x ./install.sh \
    && ./install.sh

ENV CONFIG_PATH /data/options.json

COPY run.sh /

ENTRYPOINT ["/run.sh"]
