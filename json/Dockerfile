FROM alpine:latest

RUN apk --update --no-cache add jq nodejs-npm \
    && rm -rf /var/cache/apk/*
    
RUN npm install -g jsonlint \
    && npm install -g prettyjson
