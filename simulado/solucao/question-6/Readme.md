## Question 6 | Storage, PV, PVC, Pod volume | Solution

1. Criar o volume

```bash
k -f pv.yaml create
```

2. Criar o pvc

```bash
k -f pvc.yaml create
```

3. Criar o deployment

```bash
k -f deploy.yaml create
```

4. Confirmando a montagem

```bash
k -n project-tiger describe pod safari-5cbf46d6d-mjhsb
| grep -A2 Mounts:
```