## Desafio 8

```bash
kubectl cordon worker-node-1
kubectl create deplou nginx-deploy --image=nginx:1.16 --replicas=8
kubectl uncordon worker-node-1
```