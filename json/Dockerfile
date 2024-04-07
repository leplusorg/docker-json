FROM alpine:3.19.1

# hadolint ignore=DL3013,DL3016,DL3018
RUN apk --update --no-cache add \
    check-jsonschema \
    convert2json \
    jq \
    json2tsv \
    npm \
    openssl \
    py3-setuptools \
    py3-pip \
    toml2json \
    && rm -rf /var/cache/apk/* \
    && npm install -g jsonlint \
    && npm install -g prettyjson \
    && npm install -g jwt-cli \
    && pip3 install --no-cache-dir --upgrade --break-system-packages json2yaml pyjwt
