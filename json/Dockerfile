FROM alpine:latest

RUN apk --update --no-cache add jq npm \
    && rm -rf /var/cache/apk/*
    
RUN npm install -g jsonlint \
    && npm install -g prettyjson

RUN pip3 install --no-cache-dir json2yaml
