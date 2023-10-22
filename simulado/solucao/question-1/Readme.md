## Question 1 | Contexts | Solution

1. Listar contextos

```bash
k config get-contexts -o name
```

2. Pegar o contexto que está ativo utilizando o comando `kubectl`

```bash
kubectl config current-context
```

3. Pegar o contexto que está ativo utilizando sem comando `kubectl` 

```bash
cat ~/.kube/config | grep current
```