## Question 5 | Kubectl sorting | Solution

1. Listar os pods por `careationTimestamp`

```bash
kubectl get pod -A --sort-by=.metadata.creationTimestamp
```

2. Listar os pods por `UID`

```bash
kubectl get pod -A --sort-by=.metadata.uid
```