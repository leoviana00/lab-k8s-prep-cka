## Question 7 | Node and Pod Resource Usage | Solution

1. Verificando as métricas sobre recursos dos nodes

```bash
k top node
```

2. Verificando as métricas sobre recursos dos pod

```bash
kubectl top pod --containers=true
```