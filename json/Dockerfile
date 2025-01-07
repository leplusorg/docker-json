FROM alpine:3.21.1@sha256:b97e2a89d0b9e4011bb88c02ddf01c544b8c781acf1f4d559e7c8f12f1047ac3

HEALTHCHECK NONE

ENTRYPOINT []

ARG USER_NAME=default
ARG USER_HOME=/home/default
ARG USER_ID=1000
ARG USER_GECOS=Default

# hadolint ignore=DL3016,DL3018
RUN apk --update --no-cache add \
    jose \
    jq \
    npm \
    openssl \
    py3-setuptools \
    py3-pip \
    && rm -rf /var/cache/apk/* \
    && npm install -g jsonlint \
    && npm install -g prettyjson \
    && npm install -g jwt-cli

# hadolint ignore=DL3013
RUN pip3 install --no-cache-dir --upgrade --break-system-packages json2yaml pyjwt

RUN adduser \
  --home "${USER_HOME}" \
  --uid "${USER_ID}" \
  --gecos "${USER_GECOS}" \
  --disabled-password \
  "${USER_NAME}"

ENV HOME="${USER_HOME}"

USER "${USER_NAME}"

WORKDIR "${HOME}"
