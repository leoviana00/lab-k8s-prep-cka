## Desafio 2

- Acessando o `Control PLane` [Master]
```bash
vagrant ssh master-01
```

<p align="center">
  <img alt="cka" src="image/lab-2/ssh-master-01.png">
</p>

- Entrando como `root`
```bash
sudo su
```

<p align="center">
  <img alt="cka" src="image/lab-2/root.png">
</p>

- Verificando o `test.kubeconfig`
```bash
cat /root/TEST/teste.kubeconfig
```

<p align="center">
  <img alt="cka" src="image/lab-2/kubeconfig.png">
</p>

- Verificando as configurações 
```bash
kubectl config view
```
<p align="center">
  <img alt="cka" src="image/lab-2/config-view.png">
</p>

- Comparando com o `teste.kubeconfig` é possível ver uma diferença na porta do server
- Config view
```bash
server: https://lb.lab.k8s.io:6443
```

- teste.kubeconfig
```bash
server: https://lb.lab.k8s.io:4380
```

- A porta configurada no `teste.kubeconfig está errada`
- Acessar o arquivo de configurações e corrigir

```bash
vim /root/TEST/teste.kubeconfig 
```
<p align="center">
  <img alt="cka" src="image/lab-2/kubeconfig-fix.png">
</p>