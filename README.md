# K8s-volumes

## EmptyDir for key value API service

```bash
kubectl apply -f https://raw.githubusercontent.com/geksogen/K8s-volumes/master/emptyDir/key_value_API/kvstore.yaml
```

```bash
kubectl -n volumes get pod -o wide
```

```bash
kubectl  get node -o wide
```

```bash
curl http://<NodeIP>:<Port>/save -d 'key=values'
curl http://<NodeIP>:<Port>/read/<key>
```

```bash
kubectl -n volumes exec <pod name> -- ls /data/
kubectl -n volumes exec <pod name> -- cat /data/<key>
```

```bash
kubectl -n volumes delete pod -l app=kvstore
kubectl -n volumes delete deployment kvstore
kubectl -n volumes delete service kvstore-service
```
## EmptyDir for init container

```bash
kubectl apply -f https://raw.githubusercontent.com/geksogen/K8s-volumes/master/emptyDir/init_container/web.yaml
```

```bash
kubectl -n volumes get pod --watch
```

```bash
kubectl -n volumes exec init-demo -- ls /usr/share/nginx/html
kubectl -n volumes exec init-demo -- cat /usr/share/nginx/html/index.html
```

```bash
kubectl -n volumes delete pod init-demo
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
kubectl patch pv my-pv -p '{"spec":{"persistentVolumeReclaimPolicy":"Retain"}}'
kubectl -n volumes exec pod -- cat /mnt/index.txt

```
[ReadWriteOncePod](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)
The volume can be mounted as read-write by a single Pod. Use ReadWriteOncePod access mode if you want to ensure that only one pod across whole cluster can read that PVC or write to it. This is only supported for CSI volumes and Kubernetes version 1.22+.


