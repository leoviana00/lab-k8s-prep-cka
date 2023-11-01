## Policy Network

1. Crie uma nova NetworkPolicy chamada allow-port-from-namespace no namespace existente colors.
2. Certifique-se de que a nova NetworkPolicy permita que os pods no namespace interno se conectem à porta 9000 dos pods no namespace colors.
3. Certifique-se ainda de que a nova NetworkPolicy:
```console
✑ não permite acesso a Pods, que não escutam na porta 9000
✑ não permite acesso de Pods, que não estão no namespace colors
```

- Testando a comunicação:
```bash
kubectl -n colors -it exec azul -- wget -O- 10.233.105.23:9000
```