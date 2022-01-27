# k3s Practices

- [x] install kubectl
- [x] create k3s env
- [ ] Summatize basic commands

## install kubectl ( for jetson )

```
snap install kubectl --classic
```

## create k3s env ( jetson single node no master node)

```
curl -sfL https://get.k3s.io | sh -s - --docker --write-kubeconfig-mode 644
export KUBECONFIG=/etc/rancher/k3s/k3s.yaml
```

## Summatize basic commands
