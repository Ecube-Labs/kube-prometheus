# kube-prometheus
[Originated from kube-prometheus](https://github.com/coreos/kube-prometheus)

## Apply the Kube-Prometheus stack
```
$ kubectl apply -f manifests/setup
$ kubectl apply -f manifests/
```

## Customizing Kube-Prometheus

### Configuration
Configure `example.jsonnet`.

**DO NOT MODIFY FILES IN THE `manifests/` FOLDER MANUALLY.**

### Installing
```
$ docker run --rm -v $(pwd):$(pwd) --workdir $(pwd) quay.io/coreos/jsonnet-ci jb update
```
`jb` downloads `kube-prometheus` dependency to `vendor` folder. 

### Compiling
```
$ docker run --rm -v $(pwd):$(pwd) --workdir $(pwd) quay.io/coreos/jsonnet-ci ./build.sh example.jsonnet
```
`build.sh` script creates a bunch of manifest files in the `manifest/` folder. Use `kubectl` to create/update kubernetes object as per your configuration:
```
$ kubectl apply -f manifests/setup
$ kubectl apply -f manifests/
```