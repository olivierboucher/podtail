# Podtail

Podtail is a Go port of Johan Haleby's [kubetail](https://github.com/johanhaleby/kubetail) utilty which now also allows Windows users to aggregate (tail/follow) logs from multiple pods into one stream.

This is the same as running "kubectl logs -f <pod>" but for multiple pods.

## Compatibility with kubetail

The following checklist details which flags/options are currently supported:

- [x] `-h, --help`
- [ ] `-c, --container`
- [x] `-t, --context`
- [x] `-l, --selector`
- [x] `-n, --namespace`
- [x] `-s, --since`
- [ ] `-b, --line-buffered`
- [x] `-e, --regex`
- [ ] `-j, --jq`
- [ ] `-k, --colored-output`
- [ ] `-z, --skip-colors`
- [ ] `--timestamps`
- [x] `--tail`
- [x] `-v, --version`

Please raise an issue if theres an unimplemented flag you need support for.

## Installation
Podtail currently wraps the `kubectl` command which you need to have installed and available on the path in order to use `podtail`.

Please refer to the Kubernetes documentation for information on how to install `kubectl` for your specific OS.

### OSX
You use Brew to install the client as follows:

    $ brew tap johnmccabe/podtail && brew install podtail

### Windows
Just download `podtail.exe` from the [Github Releases]((https://github.com/johnmccabe/podtail/releases/) page and copy it to a location on your `%PATH%`.

### Linux
Just download `podtail.tgz` from the [Github Releases]((https://github.com/johnmccabe/podtail/releases/) page, extract and copy it to a location on your `%PATH%`.


## Usage
Details of the support flags etc can be seen using the `--help` flag.

    podtail --help

Some example commands include:

    podtail my-pod-v1
    podtail my-pod-v1 -t int1-context
    podtail '(service|consumer|thing)' -e regex
    podtail -l service=my-service
    podtail --selector service=my-service --since 10m
    podtail --tail 1