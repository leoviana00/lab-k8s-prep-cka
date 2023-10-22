## Question 4 | Pod Ready if Service is reachable | Solution

1. Criar o template para o primeiro pod

```bash
k run ready-if-service-ready --image=nginx:1.16.1-alpine $do > pod1.yaml
```

2. Criar o pod

```bash
k -f pod1.yaml create
```

3. Checar de o pod subiu

```bash
k get pod ready-if-service-ready
```

- Usando describe
```bash
k describe pod ready-if-service-ready
```

4. Criar o segundo pod

```bash
k run am-i-ready --image=nginx:1.16.1-alpine --labels="id=cross-server-ready"
```