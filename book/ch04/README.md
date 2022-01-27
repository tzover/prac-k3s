# Kubernetes

## kubectl

```
echo 'source <(kubectl completion zsh)' >> ~/.zshrc
```

## basic commands

```
kubectl get all
kubectl get node
kubectl get pods
kubectl get pods -o wide
kubectl get pods -o json
kubectl get pods --watch

kubectl describe pod pod-name
kubectl describe node node-name

kubectl -n kube-system get pods
kubectl -n kube-system top pod --containers

kubectl exec -it pod-name -- /bin/bash
kubectl exec -it pod-name -c container-name -- /bin/bash

kubectl logs pod-name
kubectl logs pod-name -c container-name

kubectl port-forward pod-name 8888:80

alias k=kubectl
```

> curl -I localhost:8888 or curl localhost:8888

## Kubernetes resource

| 種別                      | 概要                                                         |
| :------------------------ | :----------------------------------------------------------- |
| Workloads APIs カテゴリ   | コンテナの実行に関するリソース                               |
| Service APIs カテゴリ     | コンテナを外部公開するようなエンドポイントを提供するリソース |
| Config & Storage カテゴリ | 設定 / 機密情報 / 永続化ボリュームなどに関するリソース       |
| Cluster APIs カテゴリ     | セキュリティやクォータに関するリソース                       |
| Metadata APIs カテゴリ    | クラスタ内の他のリソースを操作するためのリソース             |

### Workloads APIs カテゴリ

> コンテナの実行に関するリソース

- Pod
- Replocation Controller
- Replicaset
- Deployment
- DaemonSet
- StatefulSet
- Job
- CronJob

### Service APIs カテゴリ

> コンテナを外部公開するようなエンドポイントを提供するリソース

- Service
  - ClusterIP
  - ExternalIP (ClusterIP)
  - NodePort
  - LoadBalancer
  - Headless (None)
  - ExternalName
  - None-Selector
- Ingress

### Config & Storage カテゴリ

> 設定 / 機密情報 / 永続化ボリュームなどに関するリソース

- Secret
- ConfigMap
- Persistent VolumeChain

### Cluster APIs カテゴリ

> セキュリティやクォータに関するリソース

- Node
- Namespace
- Persistent Volume
- ResourceQuota
- Service Account
- Role
- ClusterRole
- RoleBinding
- ClusterRoleBinding
- NetworkPolicy

### Metadata APIs カテゴリ

> クラスタ内の他のリソースを操作するためのリソース

- LimitRange
- HorizontalPodAutoscaler
- PodDisruptionBudget
- CustomResourceDefinition

## annotations

```
sudo apt install jq
```

- 確認

```
kubectl apply -f ./manufests/annotation.yml
kubectl get pod sample-annotations -o json | jq .metadata.annotations
```

- 追加 上書き 削除

```
kubectl annotate pods sample-annotations an3=test
kubectl annotate pods sample-annotations an3=newTest --overwrite
kubectl annotate pods sample-annotations an3-
```

## labels

```
sudo apt install jq
```

- 確認

```
kubectl apply -f ./manufests/label.yml
kubectl get pod sample-labels -o json | jq .metadata.labels
```

- 追加 上書き 削除

```
kubectl label pods sample-labels lb3=test
kubectl label pods sample-labels lb3=newTest --overwrite
kubectl label pods sample-labels lb3-
```
