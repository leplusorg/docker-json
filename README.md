# JSON

Multi-platform Docker container with utilities to process JSON data (`jq`, `jsonlint`, `prettyjson`, `jose`, `json2yaml`...).

[![Dockerfile](https://img.shields.io/badge/GitHub-Dockerfile-blue)](json/Dockerfile)
[![Docker Build](https://github.com/leplusorg/docker-json/workflows/Docker/badge.svg)](https://github.com/leplusorg/docker-json/actions?query=workflow:"Docker")
[![Docker Stars](https://img.shields.io/docker/stars/leplusorg/json)](https://hub.docker.com/r/leplusorg/json)
[![Docker Pulls](https://img.shields.io/docker/pulls/leplusorg/json)](https://hub.docker.com/r/leplusorg/json)
[![Docker Version](https://img.shields.io/docker/v/leplusorg/json?sort=semver)](https://hub.docker.com/r/leplusorg/json)
[![CII Best Practices](https://bestpractices.coreinfrastructure.org/projects/10070/badge)](https://bestpractices.coreinfrastructure.org/projects/10070)
[![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/leplusorg/docker-json/badge)](https://securityscorecards.dev/viewer/?uri=github.com/leplusorg/docker-json)

## Example without using the filesystem

Let's say that you have a file `foo.json` in your current working directory that you want to process with jq:

**Mac/Linux**

```bash
cat foo.json | docker run --rm -i --net=none leplusorg/json jq '.'
```

**Windows**

```batch
type foo.json | docker run --rm -i --net=none leplusorg/json jq '.'
```

## Example using the filesystem

Same thing, assuming that you have a file `foo.json` in your current working directory that you want to process with jq:

**Mac/Linux**

```bash
docker run --rm -t --user="$(id -u):$(id -g)" --net=none -v "$(pwd):/tmp" leplusorg/json jq '.' /tmp/foo.json
```

**Windows**

In `cmd`:

```batch
docker run --rm -t --net=none -v "%cd%:/tmp" leplusorg/json jq '.' /tmp/foo.json
```

In PowerShell:

```pwsh
docker run --rm -t --net=none -v "${PWD}:/tmp" leplusorg/json jq '.' /tmp/foo.json
```

## Help

To know more command-line options of `jq`:

```bash
docker run --rm --net=none leplusorg/json jq -h
```

## Software Bill of Materials (SBOM)

To get the SBOM for the latest image (in SPDX JSON format), use the
following command:

```bash
docker buildx imagetools inspect leplusorg/json --format '{{ json (index .SBOM "linux/amd64").SPDX }}'
```

Replace `linux/amd64` by the desired platform (`linux/amd64`, `linux/arm64` etc.).

### Sigstore

[Sigstore](https://docs.sigstore.dev) is trying to improve supply
chain security by allowing you to verify the origin of an
artifcat. You can verify that the jar that you use was actually
produced by this repository. This means that if you verify the
signature of the ristretto jar, you can trust the integrity of the
whole supply chain from code source, to CI/CD build, to distribution
on Maven Central or whever you got the jar from.

You can use the following command to verify the latest image using its
sigstore signature attestation:

```bash
cosign verify leplusorg/json --certificate-identity-regexp 'https://github\.com/leplusorg/docker-json/\.github/workflows/.+' --certificate-oidc-issuer 'https://token.actions.githubusercontent.com'
```

The output should look something like this:

```text
Verification for index.docker.io/leplusorg/xml:main --
The following checks were performed on each of these signatures:
  - The cosign claims were validated
  - Existence of the claims in the transparency log was verified offline
  - The code-signing certificate was verified using trusted certificate authority certificates

[{"critical":...
```

For instructions on how to install `cosign`, please read this [documentation](https://docs.sigstore.dev/cosign/system_config/installation/).

## Request new tool

Please use [this link](https://github.com/leplusorg/docker-json/issues/new?assignees=thomasleplus&labels=enhancement&template=feature_request.md&title=%5BFEAT%5D) (GitHub account required) to request that a new tool be added to the image. I am always interested in adding new capabilities to these images.
