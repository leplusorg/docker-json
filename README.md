# JSON

Docker container with utilities to process JSON data (jq, jsonlint...).

[![Docker Build](https://github.com/leplusorg/docker-json/workflows/Docker/badge.svg)](https://github.com/leplusorg/docker-json/actions?query=workflow:"Docker")
[![Docker Stars](https://img.shields.io/docker/stars/leplusorg/json)](https://hub.docker.com/r/leplusorg/json)
[![Docker Pulls](https://img.shields.io/docker/pulls/leplusorg/json)](https://hub.docker.com/r/leplusorg/json)
[![Docker Automated](https://img.shields.io/docker/cloud/automated/leplusorg/json)](https://hub.docker.com/r/leplusorg/json)
[![Docker Build](https://img.shields.io/docker/cloud/build/leplusorg/json)](https://hub.docker.com/r/leplusorg/json)
[![Docker Version](https://img.shields.io/docker/v/leplusorg/json?sort=semver)](https://hub.docker.com/r/leplusorg/json)

## Example without using the filesystem

Let's say that you have a file `foo.json` in your current working directory that you want to process with jq:

### Mac/Linux

```
cat foo.json | docker run --rm -i --net=none leplusorg/json jq '.'
```

### Windows

```
type foo.json | docker run --rm -i --net=none leplusorg/json jq '.'
```

## Example using the filesystem

Same thing, assuming that you have a file `foo.json` in your current working directory that you want to process with jq:

### Mac/Linux

```
docker run --rm -t --user="$(id -u):$(id -g)" --net=none -v "$(pwd):/tmp" leplusorg/json jq '.' /tmp/foo.json
```

### Windows

In `cmd`:

```
docker run --rm -t --net=none -v "%cd%:/tmp" leplusorg/json jq '.' /tmp/foo.json
```

In PowerShell:

```
docker run --rm -t --net=none -v "${PWD}:/tmp" leplusorg/json jq '.' /tmp/foo.json
```

## Help

To know more command line options of `jq`:

```
docker run --rm --net=none leplusorg/json jq -h
```

## Request new tool

Please use [this link](https://github.com/leplusorg/docker-json/issues/new?assignees=leplusorg&labels=enhancement&template=feature_request.md&title=%5BFEAT%5D) (GitHub account required) to request that a new tool be added to the image. I am always interested in adding new capabilities to these images.
