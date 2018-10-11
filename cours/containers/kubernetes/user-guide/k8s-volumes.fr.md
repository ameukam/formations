### Kubernetes : Volumes

- Fournir du stockage persistent aux PODs
- Fonctionnent de la même façon que les volumes Docker pour les volumes hôte :
    - EmptyDir ~= volumes docker
    - HostPath ~= volumes hôte
- Support de multiples backend de stockage :
    - GCE : PD
    - AWS : EBS
<<<<<<< HEAD
    - glusterFS / NFS
=======
    - GlusterFS / NFS
>>>>>>> 8dad3d5aeb4b7504739cce981b868470d17f1a16
    - Ceph
    - iSCSI

### Kubernetes : Volumes

- On déclare d'abord le volume et on l'affecte à un service :

<<<<<<< HEAD
```
=======
```yaml
>>>>>>> 8dad3d5aeb4b7504739cce981b868470d17f1a16
apiVersion: v1
kind: Pod
metadata:
  name: redis
spec:
  containers:
  - name: redis
    image: redis
    volumeMounts:
    - name: redis-persistent-storage
      mountPath: /data/redis
  volumes:
  - name: redis-persistent-storage
    emptyDir: {}
```

### Kubernetes : Storage Class

<<<<<<< HEAD
- permet de définir les différents types de stockage disponibles
- utilisé par les `PersistentVolumes` pour solliciter un espace de stockage au travers des `PersistentVolumeClaims`
=======
- Permet de définir les différents types de stockage disponibles
- Utilisé par les `Persistent Volumes` pour solliciter un espace de stockage au travers des `Persistent Volume Claims`
>>>>>>> 8dad3d5aeb4b7504739cce981b868470d17f1a16


### Kubernetes : Storage Class

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: slow
provisioner: kubernetes.io/aws-ebs
parameters:
  type: io1
  zones: us-east-1d, us-east-1c
  iopsPerGB: "10"
```

<<<<<<< HEAD
### Kubernetes : PervistentVolumeClaims
=======
### Kubernetes : PersistentVolumeClaims
>>>>>>> 8dad3d5aeb4b7504739cce981b868470d17f1a16

- Ressource utilisée et vue comme une requête pour solliciter du stockage persistant
- Offre aux PV une variété d'options en fonction du cas d'utilisation
- Utilisé par les `StatefulSets` pour solliciter du stockage (Utilisaltion du champ `volumeClaimTemplates`)

<<<<<<< HEAD
### Kubernetes : PervistentVolumeClaims
=======
### Kubernetes : PersistentVolumeClaims
>>>>>>> 8dad3d5aeb4b7504739cce981b868470d17f1a16

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
    name: storage-claim
spec:
    accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 5Gi
  storageClassName: "slowl"
<<<<<<< HEAD
=======
  selector:
    matchLabels:
      release: "stable"
    matchExpressions:
      - {key: capacity, operator: In, values: [10Gi, 20Gi]}
>>>>>>> 8dad3d5aeb4b7504739cce981b868470d17f1a16
```

### Kubernetes : PersistentVolume

- Composant de stockage dans le cluster kubernetes
- Stockage externe aux noeuds du cluster
- Cycle de vie d'indépendant du pod qui le consomme
- Peut être provisionné manuellement par un administrateur ou dynamiquement grâce un `StorageClass`

### Kubernetes : PersistentVolume

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: persistent-volume-1
spec:
  storageClassName: slow
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/tmp/data"
```

