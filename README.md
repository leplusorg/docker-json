# JSON

Docker container with utilities to process JSON data (jq, jsonlint...).

## Example without using the filesystem

Let's say that you have a file `foo.json` in your current working directory that you want to process with jq:

### Mac/Linux

```
cat foo.json | docker run --rm -it --net=none thomasleplus/json jq '.'
```

### Windows

```
type foo.json | docker run --rm -it --net=none thomasleplus/json jq '.'
```

## Example using the filesystem

Same thing, assuming that you have a file `foo.json` in your current working directory that you want to process with jq:

### Mac/Linux

```
docker run --rm -it --user="$(id -u):$(id -g)" --net=none -v "$(pwd):/tmp" thomasleplus/json jq '.' /tmp/foo.json
```

### Windows

In `cmd`:

```
docker run --rm -it --net=none -v "%cd%:/tmp" thomasleplus/json jq '.' /tmp/foo.json
```

In PowerShell:

```
docker run --rm -it --net=none -v "${PWD}:/tmp" thomasleplus/json jq '.' /tmp/foo.json
```

## Help

To know more command line options of `jq`:

```
docker run --rm -it --net=none thomasleplus/json jq -h
```
