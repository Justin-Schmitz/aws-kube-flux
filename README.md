# aws-kube-flux

Created it from [bearengineer/awscli-kubectl GitHub repo](https://github.com/bearengineer/awscli-kubectl) as a base because WSL2 sucks sometimes and I need to get work done.

# What is awscli?

> Awscli is the Amazon web services command line interface.

[Overview of awscli](https://docs.aws.amazon.com/cli/index.html)

# What is Kubectl?

> Kubectl is the Kubernetes command line interface.

[Overview of kubectl](https://kubernetes.io/docs/reference/kubectl/overview/)

# What is Fluxctl?

> Fluxctl provides an API that can be used from the command line.

[Overview of fluxctl](https://fluxcd.io/legacy/flux/references/fluxctl/)

# TL;DR;

```bash
$ docker run -ti --rm ilikedocking/aws-kube-flux
```

```bash
$ docker run -ti -e 'AWS_ACCESS_KEY_ID=********************' -e 'AWS_SECRET_ACCESS_KEY=****************************************' -v '/Users/ilikedocking/.kube:/root/.kube' --rm ilikedocking/aws-kube-flux kubectl get pods --all-namespaces
```

```bash
$ docker run -ti -v '/Users/ilikedocking/.aws:/root/.aws' -v '/Users/ilikedocking/.kube:/root/.kube' --rm ilikedocking/aws-kube-flux kubectl get pods --all-namespaces
```


# Supported tags and respective `Dockerfile` links

* [`latest` (Dockerfile)](https://github.com/Justin-Schmitz/aws-kube-flux/blob/Dockerfile)

Subscribe to project updates by watching the [Justin-Schmitz/aws-kube-flux GitHub repo](https://github.com/Justin-Schmitz/aws-kube-flux).

# Get this image

The recommended way to get the aws-kube-flux Docker Image is to pull the prebuilt image from the [Docker Hub Registry](https://hub.docker.com/u/ilikedocking/aws-kube-flux).

```bash
$ docker pull ilikedocking/aws-kube-flux:latest
```

If you wish, you can also build the image yourself.

```bash
$ docker build -t ilikedocking/aws-kube-flux:latest 'https://github.com/Justin-Schmitz/aws-kube-flux.git#master'
```

# Configuration

## Running commands

To run commands inside this container you can use `docker run`, for example to execute `kubectl --version` you can follow the example below:

```bash
$ docker run --rm --name kubectl ilikedocking/aws-kube-flux:latest -- kubectl version
```

Consult the [Kubectl Reference Documentation](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) or the [AWS CLI Reference Documentation](https://docs.aws.amazon.com/cli/index.html) or the [FLUXCTL CLI Reference Documentation](https://fluxcd.io/legacy/flux/references/fluxctl/)  to find the completed list of commands available.

## AWS Credentials

AWS credentials can either be passed by environment variables, or by mounting a volume with aws credentials file under `/root/.aws`.

### Environment variables

```bash
$ docker run -ti -e 'AWS_ACCESS_KEY_ID=********************' -e 'AWS_SECRET_ACCESS_KEY=****************************************' --rm ilikedocking/aws-kube-flux aws s3 ls
```

### AWS directory

```bash
docker run -ti -v '/Users/ilikedocking/.aws:/root/.aws' --rm ilikedocking/aws-kube-flux aws s3
```

## Kubectl credentials

Kubectl credentials can be passed by mounting a volume with the kubeconfig under `/root/.kube`.

### Kubectl directory

```bash
docker run -ti -v '/Users/ilikedocking/.kube:/root/.kube' --rm ilikedocking/aws-kube-flux kubectl get pods
```

# Contributing

We'd love for you to contribute to this container. You can request new features by creating an [issue](https://github.com/Justin-Schmitz/aws-kube-flux/issues), or submit a [pull request](https://github.com/Justin-Schmitz/aws-kube-flux/pulls) with your contribution.

# Issues

If you encountered a problem running this container, you can attempt to fix it yourself --> and then let me know and I'll update the container.

# License

Copyright (c) 2022. All rights reserved.

This work is licensed under the terms of the MIT license.  
For a copy, see <https://opensource.org/licenses/MIT>.

