# Kubectl KCL Plugin

[![Go Report Card](https://goreportcard.com/badge/github.com/kcl-lang/kubectl-kcl)](https://goreportcard.com/report/github.com/kcl-lang/kubectl-kcl)
[![GoDoc](https://godoc.org/github.com/kcl-lang/kubectl-kcl?status.svg)](https://godoc.org/github.com/kcl-lang/kubectl-kcl)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://github.com/kcl-lang/kubectl-kcl/blob/main/LICENSE)
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fkcl-lang%2Fkubectl-kcl.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2Fkcl-lang%2Fkubectl-kcl?ref=badge_shield)

[KCL](https://github.com/kcl-lang/kcl) is a constraint-based record & functional domain language. Full documents of KCL can be found [here](https://kcl-lang.io/).

This project is a `kubectl` plugin to generate, mutate and validate Kubernetes manifests using the KCL programming language.

## Installation

Use this as a `kubectl` plugin.

### From Krew Index

Add to `krew` index and install with:

```shell
kubectl krew index add kubectl-kcl https://github.com/kcl-lang/kubectl-kcl
kubectl krew install kubectl-kcl/kubectl-kcl
```

### From GitHub Releases

Download the binary from GitHub releases, then copy the `kubectl-kcl` binary to your `PATH`. If not, you can also use the binary standalone.

## Usage

```shell
kubectl kcl run -f ./examples/kcl-run.yaml
```

## Developing

### Prerequisites

+ GoLang 1.21+

```shell
git clone https://github.com/kcl-lang/kubectl-kcl.git
cd kubectl-kcl
go run main.go
```

### Test

#### Unit Test

```shell
go test ./...
```

#### Integration Test

```shell
go run main.go run -f ./examples/kcl-run.yaml
```

## Guides for Developing KCL

Here's what you can do in the KCL script:

+ Read resources from `option("resource_list")`. The `option("resource_list")` complies with the [KRM Functions Specification](https://kpt.dev/book/05-developing-functions/01-functions-specification). You can read the input resources from `option("resource_list")["items"]` and the `functionConfig` from `option("resource_list")["functionConfig"]`.
+ Return a KPM list for output resources.
+ Return an error using `assert {condition}, {error_message}`.
+ Read the environment variables. e.g. `option("PATH")` (Not yet implemented).
+ Read the OpenAPI schema. e.g. `option("open_api")["definitions"]["io.k8s.api.apps.v1.Deployment"]` (Not yet implemented).

Full documents of KCL can be found [here](https://kcl-lang.io/).


## License
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fkcl-lang%2Fkubectl-kcl.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2Fkcl-lang%2Fkubectl-kcl?ref=badge_large)