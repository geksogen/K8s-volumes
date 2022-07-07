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
kubectl exec <pod name> -- ls /data/
kubectl exec <pod name> -- cat /data/<key>
```

```bash
kubectl delete pod -l app=kvstore
```
## emptyDir for init container

```bash
kubectl apply -f https://raw.githubusercontent.com/geksogen/K8s-volumes/master/emptyDir/init_container/web.yaml
```

```bash
kubectl get pod --watch
```

```bash
kubectl exec init-demo -- ls /usr/share/nginx/html
kubectl exec init-demo -- cat /usr/share/nginx/html/index.html
```

## persistentVolume

```bash
kubectl apply -f https://raw.githubusercontent.com/geksogen/K8s-volumes/master/persistentvolume/pv.yaml
```

```bash
kubectl get pv
```

```bash
kubectl apply -f https://raw.githubusercontent.com/geksogen/K8s-volumes/master/persistentvolume/pvc.yaml
```

## statefilset