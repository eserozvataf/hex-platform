# 🧱 hex-platform

## What is this?

This repository consists of Hex-Platform's "infrastructure as code" definitions.

Hex-Platform is simply a bundle consists of components, which are configured to work together, in order to enable functions-as-a-service execution on your newly created or existing kubernetes cluster.

Hex-Platform utilizes [terraform](https://terraform.io) to apply its installation/configuration to target kubernetes cluster.


## Components

- Terraform
- Ambassador Edge Stack (north-south)
- Prometheus (metrics server)
- Linkerd (service mesh)
  - Grafana
  - Jaeger
- Knative


## Quick start

Ensure that `curl`, `kubectl` and `terraform` is installed on your system first.

Clone this git repo `git clone
   https://github.com/eserozvataf/hex-platform.git` - and checkout the [tagged
   release](https://github.com/eserozvataf/hex-platform/releases) you'd like to
   use.

Then run the command below,

```sh
$ ./bin/installer
```


### Ambassador Edge Stack Dashboard

Download edgectl first, and then:

```sh
$ edgectl login --namespace=ambassador --context=docker-desktop localhost
```


### Linkerd Dashboard

Download linkerd first, and then:

```sh
$ linkerd dashboard --context docker-desktop
```


### Knative FaaS Sample

Deploy the helloworld knative application container:

```sh
$ kubectl apply -f etc/knative-faas-sample/helloworld-service.yml
```

Then forward the port and make a request:

```sh
$ kubectl port-forward -n ambassador svc/ambassador 80
$ curl -k -H "Host: helloworld.default.example.com" https://localhost
```


## Todo List

See [GitHub Projects](https://github.com/eserozvataf/hex-platform/projects) for more.


## Requirements

* Bash-compatible shell
* cURL
* Kubectl
* Terraform (https://terraform.io/)


## License

Apache 2.0, for further details, please see [LICENSE](LICENSE) file.


## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for details.

It is publicly open for any contribution. Bugfixes, new features and extra modules are welcome.

* To contribute to code: Fork the repo, push your changes to your fork, and submit a pull request.
* To report a bug: If something does not work, please report it using [GitHub Issues](https://github.com/eserozvataf/hex-platform/issues).


## To Support

[Visit my patreon profile at patreon.com/eserozvataf](https://www.patreon.com/eserozvataf)
