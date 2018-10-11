### Kubectl : Advanced Usage

<<<<<<< HEAD
- Il est possible de mettre à jour un service sans incident grâce ce qui est appelé le _rolling-update_.
- Avec les _rolling updates_, les resources qu'expose un objet `Service` se mettent à jour progressivement.
- Seuls les objets `Deployments`, `DaemonSet` et `StatefulSet` support les _rolling updates_.
- Les arguments `maxSurge` et `maxUnavailabe` définissent le rythme du _rolling update_.
- La commande `kubectl rollout` permet de suivre les _rolling updates_ effectués.
=======
- Il est possible de mettre à jour un service sans incident grâce ce qui est appelé le _rolling-update_. 
- Avec les _rolling updates_, les resources qu'expose un objet `Service` se mettent à jour progressivement.
- Seuls les objets `Deployments`, `DaemonSet` et `StatefulSet` support les _rolling updates_.
- Les arguments `maxSurge` et `maxUnavailabe` définissent le rythme du _rolling update_.
- La commande `kubectl rollout` permet de suivre les _rolling updates_ éffectués.
>>>>>>> 8dad3d5aeb4b7504739cce981b868470d17f1a16

### Kubectl : Advanced Usage

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx
spec:
  selector:
    matchLabels:
      app: frontend
  replicas: 2
  strategy:
    rollingUpdate:
      maxSurge: 1
      maxUnavailable: 0
    type: RollingUpdate
  template:
    metadata:
      name: nginx
      labels:
        app: frontend
    spec:
      containers:
        - image: nginx:1.9.1
          name: nginx
```

### Kubectl : Advanced Usage

```console
$ kubectl create -f nginx.yaml --record
deployment.apps/nginx created
```

### Kubectl : Advanced Usage

<<<<<<< HEAD
- il est possible d'augmenter le nombre de pods :
`kubectl scale --replicas=5 deployment nginx`

- il est possible de changer l'image d'un container utilisée par un _Deployment_ :
`kubectl set image deploy nginx nginx=nginx:1.15`

### Kubectl : Logging

=======
- Il est possible d'augmenter le nombre de pods avec la commande `kubectl scale` :
`kubectl scale --replicas=5 deployment nginx`

- Il est possible de changer l'image d'un container utilisée par un _Deployment_ : 
`kubectl set image deployment nginx nginx=nginx:1.15`

### Kubectl : Advanced Usage 

- Dry run. Afficher les objets de l'API correspondant sans les créer :
`kubectl run nginx --image=nginx --dry-run`
  
- Démarrer un container en utiliser une commande différente et des arguments différents :
```console
kubectl run nginx --image=nginx \
--command -- <cmd> <arg1> ... <argN>
```

- Démarrer un Cron Job qui calcule π et l'affiche toutes les 5 minutes :
```console
kubectl run pi --schedule="0/5 * * * ?" --image=perl --restart=OnFailure \
-- perl -Mbignum=bpi -wle 'print bpi(2000)'
```


### Kubectl : Advanced Usage

- Accéder à la console d'un container :
`kubectl run -i --tty busybox --image=busybox -- sh`

- S'attacher à un container existant :
`kubectl attach my-pod -i `

- Accéder en local à un service via un port
`kubectl port-forward my-svc 6000`


### Kubectl : Logging

- Utiliser `kubectl` pour diagnostiquer les applications et le cluster kubernetes :

kubectl cluster-info <br/>
kubectl get events  <br/>
kubectl describe node <NODE_NAME> <br/>
kubectl  logs (-f) <POD_NAME> <br/>


### Kubectl : Maintenance

- Obtenir la liste des noeuds ainsi que les informations détaillées :

```console
# kubectl get nodes
# kubectl describe nodes
```

### Kubectl : Maintenance

- Marquer le noeud comme _unschedulable_ (+ drainer les pods) et _schedulable_ :

```
kubectl cordon <NODE_NAME>
kubectl drain <NDOE_NAME>
kubectl uncordon <NODE_NAME>
```

### LimitRanges

- L'objet `LimitRange` permet de définir les valeurs minimum et maximum pour les ressources utilisées par les containers et les pods
- L'objet `LimitRange` ne s'applique dans un seul `namespace` mais peut être utilisé pour d'autres `namespaces`
- Les limites spécifiées s'appliquent à chaque pod/container créé dans le `namespace`
- Le `LimitRange` ne limite pas le nombre total de ressources disponibles dans le namespace


### LimitRanges 

```yaml
apiVersion: v1
kind: LimitRange
metadata:
  name: limit-example
spec:
  limits:
  - default:
      memory: 512Mi
    defaultRequest:
      memory: 256 Mi
    type: Container
```

### ResourceQuotas

- Un objet `ResourceQuota` limite le total des ressources de calcul consommées par les pods ainsi que
  le total de l'espace de stockage consommé par les `PersistentVolumeClaims` dans un namespace
- Il permet aussi de limiter le nombre de `pods`, `PVCs` et autres objets qui peuvent être créés dans un `namespace`

### ResourceQuotas 

```yaml
apiVersion: v1
kind: ResourceQuota
metadata:
  name: cpu-and-ram
spec:
  hard:
    requests.cpu: 400m
    requests.memory: 200Mi
    limits.cpu: 600m
    limits.memory: 500Mi
```
>>>>>>> 8dad3d5aeb4b7504739cce981b868470d17f1a16

