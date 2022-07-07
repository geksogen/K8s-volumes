# K8s-volumes

## EmptyDir for key value API service

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
## EmptyDir for init container

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

## StatefulSet

```bash
kubectl apply -f https://raw.githubusercontent.com/geksogen/K8s-volumes/master/statefulSet/web.yaml
```

```bash
kubectl get ep
```

```bash
kubectl run mycurlpod --image=curlimages/curl -i --tty -- sh
```

###Потыкаем statefullset

####Связаность по DNS имени

```bash
kubectl run -it --image busybox:1.28 my-dns-test-pod --restart=Never --rm 
/ # for i in 0 1 2;do nslookup web-$i.nginx;echo;echo '---';done
```
Делаем скрин с IP и DNS

```bash
kubectl delete pod -l app=nginx
```

```bash
kubectl run -it --image busybox:1.28 my-dns-test-pod --restart=Never --rm 
/ # for i in 0 1 2;do nslookup web-$i.nginx;echo;echo '---';done
```

####Scale up

```bash
kubectl scale sts web --replicas=5
```

####Scale down

```bash
kubectl scale sts web --replicas=3
```

####Deleting StatefulSets

```bash
kubectl delete statefulset web
```

```bash
kubectl delete sts web --cascade=false    
```

```bash
kubectl -n otus-volume delete pvc --all
```


https://www.mirantis.com/blog/multi-container-pods-and-container-communication-in-kubernetes/
https://www.bogotobogo.com/DevOps/Docker/Docker_Kubernetes_StatefulSet.php
