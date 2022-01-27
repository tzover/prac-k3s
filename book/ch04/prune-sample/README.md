# 動作確認方法

```
kubectl apply -f book/ch04/prune-sample --prune -l system=a
rm book/ch04/prune-sample/sample-pod1.yml
kubectl apply -f book/ch04/prune-sample --prune -l system=a
```

> pod/myapp2 unchanged <br>
> pod/myapp1 pruned
