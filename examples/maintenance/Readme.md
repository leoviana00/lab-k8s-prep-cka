## Upgrade Cluster Kubernetes

1. Preparação do node para manutenção
```bash
kubectl drain <node-to-drain> --ignore-daemonsets
```


2. Atualização do S.O
```bash
apt update
apt-cache madison kubeadm
```


3. Atualizando o kubeadm
```bash
apt-mark unhold kubeadm && \
apt-get update && apt-get install -y kubeadm=1.27.0-00 && \
apt-mark hold kubeadm
```


4. Verificando a versão do kubeadm
```bash
kubeadm version
```


5. Upgrade `controlplane`
```bash
kubeadm upgrade plan
sudo kubeadm upgrade apply v1.27.x
```

6. Upgrade `nodes` 
sudo kubeadm upgrade node

7. Atualizar `kubelet` e `kubectl`
```bash
apt-mark unhold kubelet kubectl && \
apt-get update && apt-get install -y kubelet=1.27.0-00 kubectl=1.27.0-00 && \
apt-mark hold kubelet kubectl
```


8. Restart
```bash
sudo systemctl daemon-reload
sudo systemctl restart kubelet 
```
                                 

9. Ativar o node para receber pods
```bash
kubectl uncordon node
```


10. Checando os node
```bash
kubectl get nodes
```


## Backup ETCD

1. Criar um `snapshot` - ETCD `stack`
ETCDCTL_API=3 etcdctl --endpoints=https://127.0.0.1:2379 \
  --cacert=/etc/kubernetes/pki/etcd/ca.crt --cert=/etc/kubernetes/pki/etcd/server.crt --key=/etc/kubernetes/pki/etcd/server.key \
  snapshot save /opt/snapshot-pre-boot.db


1. Criar `snapshot` - ETCD `externo`
ETCDCTL_API=3 etcdctl --endpoints=https://192.41.139.20:2379 \
--cacert=/etc/kubernetes/pki/etcd/ca.crt \
--cert=/etc/kubernetes/pki/etcd/server.crt \
--key=/etc/kubernetes/pki/etcd/server.key \
snapshot save /opt/cluster1.db

## Restore ETCD

1. Restore do backup
```bash
ETCDCTL_API=3 etcdctl --data-dir="/var/lib/etcd-backup" \
--endpoints=https://192.41.139.20:2379 \
--cacert=/etc/kubernetes/pki/etcd/ca.crt \
--cert=/etc/kubernetes/pki/etcd/server.crt \
--key=/etc/kubernetes/pki/etcd/server.key \
snapshot restore /opt/snapshot-pre-boot.db
```


2. Apontar o volume para o volume para o local onde está o restore

```bash
vi /etc/kubernetes/manifests/etcd.yaml
```

- `TODO`: DOCUMENTAR MELHOR O PROCEDIMENTO PARA ETCD EXTERNO