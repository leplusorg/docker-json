FROM alpine:3.15.1

# hadolint ignore=DL3013,DL3016,DL3018
RUN apk --update --no-cache add \
    jq \
    npm \
    openssl \
    py3-setuptools \
    py3-pip \
    && rm -rf /var/cache/apk/* \
    && npm install -g jsonlint \
    && npm install -g prettyjson \
    && npm install -g jwt-cli \
    && pip3 install --no-cache-dir --upgrade json2yaml pyjwt
