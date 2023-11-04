## RBAC

- Criar um namespace

```bash
kubectl create namespace space-rules
```

- Criar um serviceaccount em um namespace espcífico

```bash
kubectl -n space-rules create sa teste-viana
```

- Criar uma ClusterRole capaz de somente listar pod

```bash
kubectl create clusterrole teste-viana --verb=list --reource=pod
```

- Criar um Rolebinding para vincular a ClusterRole à serviceaccount

```bash
kubectl create rolebinding teste-viana --clusterrole=teste-viana --serviceaccount=space-rules:teste-viana
```

- Testando a listagem de pods

```bash
kubectl auth can-i list pod --as system:serviceaccount:space-rules:teste-viana
```