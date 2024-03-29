# kubernets
### Installation

```
sudo su
apt-get update
```
```
#Need to intra cluster communication
apt-get install apt-transport-https
```
#### Docker Installation
```
apt install docker.io -y
docker --version
systemctl start docker
systemctl enable docker
```
#### Kubernetes Installation
```
sudo curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add 
```
```
nano /etc/apt/sources.list.d/kubernetes.list
#Enter below line in above file
deb http://apt.kubernetes.io/ kubernetes-xenial main
```

```
apt-get update
apt-get install -y kubelet kubeadm kubectl kubernetes-cni
```

*BOOTSTRAPPING THE MASTER NODE (IN MASTER)*
```
kubeadm init

#if Error occured follow below steps
apt remove --purge kubelet
apt install -y kubeadm kubelet=1.25.5-00

wget https://github.com/containerd/containerd/releases/download/v1.6.12/containerd-1.6.12-linux-amd64.tar.gz
tar xvf containerd-1.6.12-linux-amd64.tar.gz
systemctl stop containerd
cd bin
cp * /usr/bin/
systemctl start containerd

 ```

*COPY THE COMMAND TO RUN IN MASTER & SAVE IN NOTEPAD*
```
mkdir -p $HOME/.kube
cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
```
```
chown $(id -u):$(id -g) $HOME/.kube/config
```
```
kubectl apply -f https://raw.githubusercontent.com/cor...

kubectl apply -f https://raw.githubusercontent.com/cor...
```

*CONFIGURE WORKER NODES (IN NODES)*

*COPY LONG CODE PROVIDED MY MASTER IN NODE NOW LIKE CODE GIVEN BELOW*

```
e.g- kubeadm join 172.31.6.165:6443 --token kl9fhu.co2n90v3rxtqllrs --discovery-token-ca-cert-hash sha256:b0f8003d23dbf445e0132a53d7aa1922bdef8d553d9eca06e65c928322b3e7c0
```

*GO TO MASTER AND RUN THIS COMMAND*
```
kubectl get nodes
```
