## Secrets

- Prática - Secrets como variável de ambiente

- Verificar como criar secrets

```bash
kubectl create secret generic -h
```

- Criando uma secret

```bash
kubectl create secret generic secret-db --from-literal=user=admin --from-literal=pass=admin
```

- Pegando todas as envs no pod

```bash
kubectl exec -it cka-pod-example-screts -- env 
```
- Pegando env - Filtrando pela palavra `SECRET`

```bash
kubectl exec -it cka-pod-example-screts -- env | grep SECRET
```

## Refrência

- [Secrets](https://kubernetes.io/docs/concepts/configuration/secret/)