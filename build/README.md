# docker-build-action

This GitHub action will log into the specified Docker Registry and build 1 or 2 images based on the given config.

## Config

`registry`: Registry's host

`user`: Registry's user

`password`: Registry user's password or token

`image`: Docker image name without tag

`tag`: Docker image tag

`build_args`: Environment variables passed to docker build