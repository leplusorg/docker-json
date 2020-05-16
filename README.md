# JSON

Docker container with utilities to process JSON data (jq, jsonlint...).

![GitHub Build](https://img.shields.io/github/workflow/status/thomasleplus/docker-json/Docker%20Image%20CI)
![Docker Stars](https://img.shields.io/docker/stars/thomasleplus/json)
![Docker Pulls](https://img.shields.io/docker/pulls/thomasleplus/json)
![Docker Automated](https://img.shields.io/docker/cloud/automated/thomasleplus/json)
![Docker Build](https://img.shields.io/docker/cloud/build/thomasleplus/json)
![Docker Version](https://img.shields.io/docker/v/thomasleplus/json?sort=semver)

## Example without using the filesystem

Let's say that you have a file `foo.json` in your current working directory that you want to process with jq:

### Mac/Linux

```
cat foo.json | docker run --rm -i --net=none thomasleplus/json jq '.'
```

### Windows

```
type foo.json | docker run --rm -i --net=none thomasleplus/json jq '.'
```

## Example using the filesystem

Same thing, assuming that you have a file `foo.json` in your current working directory that you want to process with jq:

### Mac/Linux

```
docker run --rm -t --user="$(id -u):$(id -g)" --net=none -v "$(pwd):/tmp" thomasleplus/json jq '.' /tmp/foo.json
```

### Windows

In `cmd`:

```
docker run --rm -t --net=none -v "%cd%:/tmp" thomasleplus/json jq '.' /tmp/foo.json
```

In PowerShell:

```
docker run --rm -t --net=none -v "${PWD}:/tmp" thomasleplus/json jq '.' /tmp/foo.json
```

## Help

To know more command line options of `jq`:

```
docker run --rm --net=none thomasleplus/json jq -h
```

## Request new tool

Please use [this link](https://github.com/thomasleplus/docker-json/issues/new?assignees=thomasleplus&labels=enhancement&template=feature_request.md&title=%5BFEAT%5D) (GitHub account required) to request that a new tool be added to the image. I am always interested in adding new capabilities to these images.
