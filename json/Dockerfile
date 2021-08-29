FROM alpine:latest

RUN apk --update --no-cache add \
    jq \
    npm \
    openssl \
    py3-setuptools \
    py3-pip \
    && rm -rf /var/cache/apk/*
    
RUN npm install -g jsonlint \
    && npm install -g prettyjson \
    && npm install -g jwt-cli

RUN pip3 install --no-cache-dir json2yaml pyjwt
