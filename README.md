# K8s-volumes

## EmptyDir for key value API service

```bash
kubectl apply -f https://raw.githubusercontent.com/geksogen/K8s-volumes/master/emptyDir/key_value_API/kvstore.yaml
```

```bash
kubectl -n guestbook get pod -o wide
```

```bash
kubectl  get node -o wide
```

```bash
curl http://<NodeIP>:<Port>/save -d 'key=values'
curl http://<NodeIP>:<Port>/read/<key>
```

```bash
kubectl -n guestbook exec <pod name> -- ls /data/
kubectl -n guestbook exec <pod name> -- cat /data/<key>
```

```bash
kubectl -n guestbook delete pod -l app=kvstore
```
## EmptyDir for init container

```bash
kubectl apply -f https://raw.githubusercontent.com/geksogen/K8s-volumes/master/emptyDir/init_container/web.yaml
```

```bash
kubectl -n guestbook get pod --watch
```

```bash
kubectl -n guestbook exec init-demo -- ls /usr/share/nginx/html
kubectl -n guestbook exec init-demo -- cat /usr/share/nginx/html/index.html
```

```bash
kubectl -n guestbook delete pod init-demo
```

## PersistentVolume

```bash
kubectl apply -f https://raw.githubusercontent.com/geksogen/K8s-volumes/master/persistentvolume/pv.yaml
```

```bash
kubectl get pv
```

```bash
kubectl apply -f https://raw.githubusercontent.com/geksogen/K8s-volumes/master/persistentvolume/pvc.yaml
```

```bash
kubectl apply -f https://raw.githubusercontent.com/geksogen/K8s-volumes/master/persistentvolume/pod.yaml
```
####Remove resource
```bash
kubectl -n volumes delete pod pod
kubectl -n volumes delete pvc myclaim
kubectl delete pv my-pv
```

####Other
```bash
kubectl run mycurlpod --image=curlimages/curl -i --tty -- sh
```


