# Helm Charts for Merbridge

> Note that the files in `deploy` are auto generated by Helm

## Install Guide

If you want to install merbridge locally with Helm:

> Note that: execute these commands in root dir of merbridge

### Install Merbridge on Istio

+ set mode=istio to switch to Istio mode, default value is `istio`.
+ set namespace where merbridge is going to install by -n .

``` bash
helm install -n istio-system merbridge helm
```

After executing this command, you will see that:

```
NAME: merbridge
LAST DEPLOYED: Mon Feb 21 01:37:40 2022
NAMESPACE: istio-system
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
Welcome to Merbridge! For more details on Merbridge, see: https://github.com/merbridge/merbridge

The Merbridge [v0.4.0] has been installed in namespace [istio-system]. It will be ready soon.

(Helm: Chart=[merbridge], Release=[merbridge], Version=[v0.4.0])
```

### Install Merbridge on Linkerd

+ set mode=linkerd to switch to linkerd mode
+ set namespace where merbridge is going to install by -n .

``` bash
helm install -n linkerd --set mode=linkerd merbridge helm
```

### Install Merbridge on Kuma

+ set mode=kuma to switch to kuma mode
+ set namespace where merbridge is going to install by -n .

``` bash
helm install -n kuma-system --set mode=kuma merbridge helm
```

### Uninstall

+ execute this command in the namespace where merbridge has been installed
+ or add -n to specific the namespace where merbridge has been installed

``` bash
helm uninstall merbridge
```

## Development

If you want to update yamls in deploy directory, please make changes into helm charts

After that, remember to update generated yamls in `deploy` directory.

``` bash
# update both istio, kuma and linkerd
make helm
# update istio deploy yaml
make helm-istio
# update linkerd deploy yaml
make helm-linkerd
# update kuma deploy yaml
make helm-kuma
# package helm charts
make helm-package
```

## TODO
- [ ] Provide Helm Repo Server to install Merbridge
