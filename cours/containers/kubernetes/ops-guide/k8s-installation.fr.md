### Installation de Kubernetes

- De nombreuses ressources présentes pour le déploiement de Kubernetes dans un environnement de production

<<<<<<< HEAD
- Un des outils est [kubeadm](https://github.com/kubernetes/kubeadm) utilisé pour rapidement démarrer un cluster kubernetes

### Installation de Kubernetes

Certains pré-requis sont nécessaires avant d'installer Kubernetes :

- Désactiver le swap
- Assurer que les ports requis soient ouverts : <https://kubernetes.io/docs/setup/independent/install-kubeadm/#check-required-ports>
- Installer Docker : <https://docs.docker.com/install>

### Installation de Kubernetes

- installer les composants Kubernetes (kubeadm, kubectl, kubelet)<https://kubernetes.io/docs/setup/independent/install-kubeadm/>
- Exécuter `sudo kubeadm init` sur le noeud master
- Exécuter `sudo kubeadm join` sur les autres noeuds (avec le token fournir par la commande `kubeadm init`)
- Copier le fichier de configuration généré par `kubeadm init`
- Installer le plugin Réseau (Dans notre cas nous utiliserons Weave)

### Installation de Kubernetes
=======
- Un des outils est [kubeadm](https://github.com/kubernetes/kubeadm) utilisé pour rapidement démarrer un cluster kubernetes 

### Installation de Kubernetes

Certains pré-requis sont nécessaires avant d'installer Kubernetes : 

- Désactiver le swap 
- Assurer que les ports requis soient ouverts : <https://kubernetes.io/docs/setup/independent/install-kubeadm/#check-required-ports>
- Installer Docker : <https://docs.docker.com/install>

### Installation de Kubernetes 

- Installer les composants Kubernetes (kubeadm, kubectl, kubelet)<https://kubernetes.io/docs/setup/independent/install-kubeadm/>
- Exécuter `sudo kubeadm init` sur le noeud master
- Exécuter `sudo kubeadm join` sur les autres noeuds (avec le token fournir par la commande `kubeadm init`)
- Copier le fichier de configuration généré par `kubeadm init`
- Installer le plugin Réseau (Dans notre cas nous utiliserons Weave Net)

### Installation de Kubernetes 
>>>>>>> 8dad3d5aeb4b7504739cce981b868470d17f1a16

Il existe des solutions managées pour Kubernetes :

- Azure Kubernetes Service : <https://azure.microsoft.com/en-us/services/kubernetes-service/>
- Google Kubernetes Engine : <https://cloud.google.com/kubernetes-engine/>
- Elastic Kubernetes Services: <https://aws.amazon.com/eks/>
- Docker for mac : <https://docs.docker.com/docker-for-mac/kubernetes/>

### Installation de Kubernetes

<<<<<<< HEAD
- via Ansible : kubespray <https://github.com/kubernetes-incubator/kubespray>
- via Terraform : <https://github.com/poseidon/typhoon>
- il existe aussi des projets open source basés sur le langage Go :
=======
- via Ansible : kubespray <https://github.com/kuberntes-incubator/kubespray>
- via Terraform : <https://github.com/poseidon/typhoon>
- Il existe aussi des projects open source basés sur le langage Go :
>>>>>>> 8dad3d5aeb4b7504739cce981b868470d17f1a16
    - kube-aws : <https://github.com/kubernetes-incubator/kube-aws>
    - kops : <https://github.com/kubernetes/kops>

### Introduction à Sonobuoy

<<<<<<< HEAD
- outil de conformité de clusters Kubernetes
- permet de facilement générer des données de diagnostics pour les applications déployées
=======
- Outil de conformité de clusters Kubernetes
- Permet de facilement générer des données de diagnostics pour les applications déployées
>>>>>>> 8dad3d5aeb4b7504739cce981b868470d17f1a16
- <https://github.com/heptio/sonobuoy/>

