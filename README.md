# Flutter Engine Binaries

Precompiled Flutter Engine binaries for custom embedders.

This is a work in progress open source translation of some internal tooling. At this stage most users would be better served by Hannes Winkler's Flutter binaries at https://github.com/ardera/flutter-ci

## Running GitHub Workflows Locally

The GitHub workflows can be run locally with [act](https://github.com/nektos/act). An `--artifact-server-path` must be provided to collect the build output. The `--platform` argument overrides the default `ubuntu-latest` runner with a non-root runner. If the platform override is omitted the build will work but tools will complain about running as root.

```
act \
    --platform ubuntu-latest=ghcr.io/catthehacker/ubuntu:runner-latest
    --artifact-server-path ./artifacts
```

A remote Docker build host can be used by setting the `DOCKER_HOST` environment variable and specifying the container architecture of the remote build host.

```
DOCKER_HOST="ssh://docker@docker.local" act \
    --container-architecture linux/amd64
    --platform ubuntu-latest=ghcr.io/catthehacker/ubuntu:runner-latest
    --artifact-server-path ./tmp
```

## TODO

- Upload artifacts as GitHub releases
- Build for multiple architectures
- Automated checks for new Flutter releases
