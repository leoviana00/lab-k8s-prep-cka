## Question 2 | Schedule Pod on Controlplane Node | Solution

1. Encontrando o `controlplane` e verificando seu taints

- Checando os nodes
```bash
k get node
```

- Checando os tains do controlplane
```bash
k describe node cluster1-controlplane1 | grep Taint -A1
```

- Checando as labels do controlplane
```bash
k get node cluster1-controlplane1 --show-labels
```

2. Criando um template para a construção do pod

```bash
k run pod1 --image=httpd:2.4.41-alpine -o yaml --dry-run=client > pod.yaml
```

3. Criando o pod

```bash
k -f pod.yaml create
```

4. Checandoo se o pod subiu no controlplane

```bash
k get pod pod1 -o wide
```