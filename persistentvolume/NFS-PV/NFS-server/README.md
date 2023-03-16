####Install
```bash
kubectl apply -f https://raw.githubusercontent.com/geksogen/K8s-volumes/master/persistentvolume/NFS-PV/NFS-server/pvc-nfs.yaml
kubectl apply -f https://raw.githubusercontent.com/geksogen/K8s-volumes/master/persistentvolume/NFS-PV/NFS-server/nfs-server.yaml
kubectl apply -f https://raw.githubusercontent.com/geksogen/K8s-volumes/master/persistentvolume/NFS-PV/NFS-server/service-nfs.yaml
kubectl apply -f https://raw.githubusercontent.com/geksogen/K8s-volumes/master/persistentvolume/NFS-PV/NFS-server/pv-nfs.yaml
```