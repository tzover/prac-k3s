## ip process

```
apt update && apt install -y iproute2 procps
ip a | grep "inet "
ss -napt | grep LISTEN
ps aux
```

## host

```
kubectl get node nxyt3 -o wide
kubectl exec -it pod-name -- hostname
kubectl exec -it pod-name -- cat /etc/resolv.conf
```

## replicaset scale

```
kubectl scale repricaset sample-rs --replicas 5
```

## replicaset

```
kubectl get replicasets -o yaml | head
```

## deployment

```
kubectl get deployments
kubectl set image deployment sample-deployment-recreate nginx-container=nginx:1.16
```

## Kubernetes Workloads API

| リソース種別          | 使い分け                                                             |
| :-------------------- | :------------------------------------------------------------------- |
| Pod                   | デバッグや確認用途などに利用する                                     |
| ReplicationController | 非推奨のため ReplicaSet を利用する                                   |
| ReplicaSet            | Pod をスケールさせて管理する。基本的には Deployment 経由で利用する   |
| Deployment            | スケールさせるワークロードに利用する                                 |
| DaemonSet             | 各ノードに 1 つずつ Pod を配置したいときに利用する                   |
| StatefulSet           | データの永続化などのステートを持つワークロードに利用する             |
| Job                   | ワークキューやタスクなどコンテナの終了が必要なワークロードに利用する |
| CronJob               | 定期的に Job を作成したいときに利用する                              |
