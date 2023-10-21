## Upgrade Cluster Kubernetes

# 1. Preparação do node para manutenção
kubectl drain <node-to-drain> --ignore-daemonsets

# Atualização do S.O
apt update
apt-cache madison kubeadm

# Atualizando o kubeadm
apt-mark unhold kubeadm && \
apt-get update && apt-get install -y kubeadm=1.27.0-00 && \
apt-mark hold kubeadm

#Verificando a versão do kubeadm
kubeadm version

# Para o controlplane
kubeadm upgrade plan
sudo kubeadm upgrade apply v1.27.x

# Para node
sudo kubeadm upgrade node

# Atualizar kubelet e kubectl
apt-mark unhold kubelet kubectl && \
apt-get update && apt-get install -y kubelet=1.27.0-00 kubectl=1.27.0-00 && \
apt-mark hold kubelet kubectl

# Restart
sudo systemctl daemon-reload
sudo systemctl restart kubelet                                  

# Ativar o node para receber pods
kubectl uncordon node

# Checando os node
kubectl get nodes

## Backup ETCD

ETCDCTL_API=3 etcdctl --endpoints=https://127.0.0.1:2379 \
  --cacert=/etc/kubernetes/pki/etcd/ca.crt --cert=/etc/kubernetes/pki/etcd/server.crt --key=/etc/kubernetes/pki/etcd/server.key \
  snapshot save /opt/snapshot-pre-boot.db


ETCDCTL_API=3 etcdctl --endpoints=https://192.41.139.20:2379 \
--cacert=/etc/kubernetes/pki/etcd/ca.crt \
--cert=/etc/kubernetes/pki/etcd/server.crt \
--key=/etc/kubernetes/pki/etcd/server.key \
snapshot save /opt/cluster1.db

## Restore ETCD

ETCDCTL_API=3 etcdctl --data-dir="/var/lib/etcd-backup" \
--endpoints=https://192.41.139.20:2379 \
--cacert=/etc/kubernetes/pki/etcd/ca.crt \
--cert=/etc/kubernetes/pki/etcd/server.crt \
--key=/etc/kubernetes/pki/etcd/server.key \
snapshot restore /opt/snapshot-pre-boot.db

## Apontar o volume para o volume para o local onde está o restore

vi /etc/kubernetes/manifests/etcd.yaml