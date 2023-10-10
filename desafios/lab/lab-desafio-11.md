## Desafio 11

- Listando meus nodes
```bash
kubectl get nodes
```

<p align="center">
  <img alt="cka" src="image/lab-11/list-nodes.png">
</p>

- Listando meus Pods no namespace `default`
```bash
kubectl get po
```

<p align="center">
  <img alt="cka" src="image/lab-11/list-pods.png">
</p>

- Listando meus Pods em todos meus namespaces
```bash
kubectl get po -A
```

<p align="center">
  <img alt="cka" src="image/lab-11/list-all-pods.png">
</p>

- Criar comando para listar todos os Pods em ordem crescente
```bash
echo "kubectl get po -A --sort-by=.metadata.creationTimestamp | tac" > /opt/pods_asc.sh
chmod +x /opt/pods_asc.sh
/opt/pods_asc.sh
```

<p align="center">
  <img alt="cka" src="image/lab-11/list-all-pods-asc.png">
</p>
