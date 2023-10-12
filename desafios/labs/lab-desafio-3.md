## Desafio 3

- Acessando o `Control PLane` [Master]
```bash
vagrant ssh master-01
```

<p align="center">
  <img alt="cka" src="image/lab-3/ssh-master-01.png">
</p>

- Entrando como `root`
```bash
sudo su
```

<p align="center">
  <img alt="cka" src="image/lab-3/root.png">
</p>

- Criando o deployment
```bash
kubectl create deploy web-proj-268 --image=nginx:1.16 
```

<p align="center">
  <img alt="cka" src="image/lab-3/deployment.png">
</p>

- Checando o deployment
```bash
kubectl get deploy
```

<p align="center">
  <img alt="cka" src="image/lab-3/get-deploy.png">
</p>

- Checando o pod
```bash
kubectl get pod
```

<p align="center">
  <img alt="cka" src="image/lab-3/get-pod.png">
</p>

- Verificando detalhes do deploy
```bash
 kubectl describe deploy web-proj-268
```

<p align="center">
  <img alt="cka" src="image/lab-3/describe-deploy.png">
</p>

- Atualizando a imagem do deployment
```bash
kubectl set image deploy web-proj-268 nginx=nginx:1.17 --record
```

<p align="center">
  <img alt="cka" src="image/lab-3/set-image-deploy.png">
</p>

- Verificando detalhes do deploy novamente
```bash
kubectl describe deploy web-proj-268
```

<p align="center">
  <img alt="cka" src="image/lab-3/update-image-describe.png">
</p>

```bash
kubectl describe deploy web-proj-268 | grep -i image
```

<p align="center">
  <img alt="cka" src="image/lab-3/deploy-describe-grep.png">
</p>

- Verificando o histórico de deployments
```bash
kubectl rollout history deploy web-proj-268
```

<p align="center">
  <img alt="cka" src="image/lab-3/history-deploy.png">
</p>

- Roll Back
```bash
kubectl rollout undo deploy web-proj-268 --to-revision=1
```

<p align="center">
  <img alt="cka" src="image/lab-3/roll-back.png">
</p>

- Verificar detalhes do deploy novamente para confirmar se a imagem voltou para a `tag: 1.16`
```bash
kubectl describe deploy web-proj-268 | grep -i image
```

<p align="center">
  <img alt="cka" src="image/lab-3/describe-roll-back.png">
</p>