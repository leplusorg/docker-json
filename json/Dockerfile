FROM alpine:3.22.0@sha256:8a1f59ffb675680d47db6337b49d22281a139e9d709335b492be023728e11715

HEALTHCHECK NONE

ENTRYPOINT []

ARG USER_NAME=default
ARG USER_HOME=/home/default
ARG USER_ID=1000
ARG USER_GECOS=Default

SHELL ["/bin/ash", "-euo", "pipefail", "-c"]

# hadolint ignore=DL3019
RUN apk -U upgrade \
    && apk add \
    jose=14-r0 \
    jq=1.8.0-r0 \
    npm=11.3.0-r0 \
    openssl=3.5.0-r0 \
    py3-pip=25.1.1-r0 \
    python3=3.12.11-r0 \
    && if apk -u list | grep -q -e . ; then \
      apk -u list ; \
      exit 1 ; \
    fi \
    && apk cache clean \
    && rm -rf /var/cache/apk/*

RUN pip3 install --no-cache-dir --upgrade --break-system-packages \
    json2yaml==1.2.0 \
    PyJWT==2.10.1 \
    && msg="$(pip3 list --outdated | grep -i -e '^json2yaml ' -e '^PyJWT ' || true)" \
    && if [ -n "${msg}" ]; then \
       >&2 echo "ERROR: outdated: ${msg}" ; \
       exit 1 ; \
    fi

RUN npm install -g \
    jsonlint@1.6.3 \
    jwt-cli@2.0.0 \
    prettyjson@1.2.5 \
    && npm outdated --global

RUN adduser \
  --home "${USER_HOME}" \
  --uid "${USER_ID}" \
  --gecos "${USER_GECOS}" \
  --disabled-password \
  "${USER_NAME}"

USER "${USER_NAME}"

ENV HOME="${USER_HOME}"

WORKDIR "${HOME}"
