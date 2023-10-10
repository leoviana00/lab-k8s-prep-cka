## 🚀 Cluster utilizado para os desafios

- Para os desafios utilizei o Cluster criado com o [Setup K8s Kubespray](../setup-k8s-kubespray/kubespray/README.md)

## 🎯 Documentação dos exercicios/desafios realizados

<details>
<summary>DESAFIO 1</summary>

1. Desafio número 1 
    - Criar um pod chamado admin-pod com uma imagem `busybox`;
    - Permitir que o pode seja capaz de definir a hora do sistema;
    - O container deve dormir por 3200 segundos;
</details>

<details>
<summary>DESAFIO 2</summary>

2. Desafio número 2:
    - Um arquivo `kubeconfig` chamado de `test.kubeconfig` foi criado em `/root/TEST`;
    - Há algo errado em sua configuração;
    - Analise e concerte ele;
</details>

<details>
<summary>DESAFIO 3</summary>

3. Desafio número 3:
    - Criar um deployment chamado `web-proj-268``, com uma imagem `nginx:1.16` e `uma replica`;
    - Depois de criado, atualize a versão da imagem no deployment para `nginx:1.17` usando `rolling update`;
    - Certifique-se de que a atualização da versão esteja registrada na anotação do recurso;
    - Verificar histórico de versões;
    - Depois faça um `rollout` do deploy;
</details>

<details>
<summary>DESAFIO 4</summary>

4. Desafio número 4:
    - Criar um novo deployment chamado `web-003`;
    - Escalar o deployment para `3 replicas`;
    - Certifique-se de que o número desejado de pods esteja sempre em execução;
</details>

<details>
<summary>DESAFIO 5</summary>

5. Desafio número 5:
    - Atualizar o Cluster (Masters e nodes) de `x.xx.x` para `x.xx.x`;
    - Certifique-se de que o número desejado do pod esteja sempre em execução
</details>

<details>
<summary>DESAFIO 6</summary>

6. Desafio número 6:
    - Criar um pod chamado `web-load-5461` usando a imagem `nginx:1.17` com o `label` configurado para `tier=web`;
</details>

<details>
<summary>DESAFIO 7</summary>

7. Desafio número 7:
    - Criar um multi container pod, `multi-pod` no namespace `desenvolvimento` usando as imagens `nginx` e `redis`;
</details>

<details>
<summary>DESAFIO 8</summary>

8. Desafio número 8:
    - Criar um novo deployment chamado `nginx-deploy` com uma imagem `nginx:1.16` com `8 replicas`;
    - Certificque-se de que nenhum pod seja implantado em um nó de trabalho: `worker-node-1`;
    - [NOTA] - Reverter as alterações realizadas
    - [Laboratório - Challenge 8](./labs/lab-desafio-8.md)
</details>

<details>
<summary>DESAFIO 9</summary>

9. Desafio número 9:
    - Criar um `ReplicaSet` (Nome: `web-pod`, Imagem `nginx:1.16` e `3 replicas`);
    - Já existe um pod em execução no cluster;
    - Certifique-se de que a contagem total do pod em execução em um cluster não seja superior a 3;
</details>

<details>
<summary>DESAFIO 10</summary>

10. Desafio número 10:
    - Existem 3 nós no cluster, crie `DaemonSet` (Nome: my-pod, imagem nginx) em cada nó, exceto um (work-node-3)
</details>

<details>
<summary>DESAFIO 11</summary>

11. Desafio número 11:

    - There are various pods running in all the namespaces of kubernetes cluster.  Write a command into `/opt/pods_asc.sh` which list all the `Pods` sorted by the `AGE` in Ascending order.

    - Existem vários pods em execução em todos os namespaces do cluster Kubernetes. Escreva um comando em `/opt/pods_asc.sh` que liste todos os `Pods` classificados por idade em ordem crescente.

    - [Laboratório - Challenge 11](./labs/lab-desafio-11.md)
</details>

<details>
<summary>DESAFIO 12</summary>

12. Desafio número 12:

    - Create a static pod on `k8s-lab-node-1` called `static-nginx` with image `nginx` and you have to make sure that it is recreated/restarted automatically in case of any failure happens.

    - Crie um pod estático em `k8s-lab-node-1` chamado `static-nginx` com a imagem `nginx` e você deve ter certeza de que ele será recriado/reiniciado automaticamente no caso de ocorrer alguma falha.

    - [Laboratório - Challenge 12](./labs/lab-desafio-12.md)
</details>

