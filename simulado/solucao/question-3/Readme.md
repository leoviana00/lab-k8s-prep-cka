## Question 3 | Scale down StatefulSet | Solution

1. Cgecando os pods `o3db`

```bash
k -n project-c13 get pod | grep o3db
```

2. Checando os recursos mais comuns para identificar qual o responsável pelos pods `o3db-*`

```bash
k -n project-c13 get deploy,ds,sts | grep o3db
```

3. Escalando os pods para 1

```bash
k -n project-c13 scale sts o3db --replicas 1
```