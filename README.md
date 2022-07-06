# K8s-volumes

## emptyDir for key value API service

```bash
kubectl apply -f https://raw.githubusercontent.com/geksogen/K8s-volumes/master/emptyDir/key_value_API/kvstore.yaml
```

```bash
kubectl get pod -o wide
```

```bash
kubectl get node -o wide
```

```bash
curl http://<NodeIP>:<Port>/save -d 'key=values'
curl http://<NodeIP>:<Port>/read/<key>
```

```bash
kubectl exec <pod name> -- ll /data/
kubectl exec <pod name> -- cat /data/<key>
```

```bash
kubectl delete pod -l app=kvstore
```

## emptyDir for init container


