## 🚀 Cluster utilizado para os desafios

- Para os desafios utilizei o Cluster criado com o [Setup K8s Kubespray](../setup-k8s-kubespray/kubespray/README.md)

## 🎯 Documentação dos exercicios/desafios realizados

<details>
<summary>CKA Challenge Question 1</summary>

1. Question
    - Create a new pod called admin-pod with image `busybox`;
    - Allow the pod to be able to set system_time;
    - The container should sleep for 3200 seconds;

    &nbsp;
    - Criar um pod chamado admin-pod com uma imagem `busybox`;
    - Permitir que o pode seja capaz de definir a hora do sistema;
    - O container deve dormir por 3200 segundos;

    &nbsp;
    - [Laboratório - Challenge 1](./labs/lab-desafio-1.md)
</details>

<details>
<summary>CKA Challenge Question 2</summary>

2. Question
    - A kubeconfig file called `est.kubeconfig` has been created in `/root/TEST`;
    - There is something wrong with configuration;
    - Troubleshoot and fix it;

    &nbsp;
    - Um arquivo `kubeconfig` chamado de `test.kubeconfig` foi criado em `/root/TEST`;
    - Há algo errado em sua configuração;
    - Analise e concerte ele;

    &nbsp;
    - [Laboratório - Challenge 2](./labs/lab-desafio-2.md)
</details>

<details>
<summary>CKA Challenge Question 3</summary>

3. Question
    - Create a new deployment called `web-proj-268`, with image `nginx:1.16` and 1 replica;
    - Next upgrade the deployment to version `1.17` using rolling update;
    - Make sure that the version upgrade is recorded in the resource annotation;

    &nbsp;
    - Criar um deployment chamado `web-proj-268`, com uma imagem `nginx:1.16` e `uma replica`;
    - Depois de criado, atualize a versão da imagem no deployment para `nginx:1.17` usando `rolling update`;
    - Certifique-se de que a atualização da versão esteja registrada na anotação do recurso;

    &nbsp;
    - Itens abaixo fora do escopo do exercicio acima: (Só para praticar mais um pouco)
        - Verificar histórico de versões;
        - Depois faça um `rollout` do deploy;

    &nbsp;
    - [Laboratório - Challenge 3](./labs/lab-desafio-3.md)
</details>

<details>
<summary>CKA Challenge Question 4</summary>

4. Question
    - Criar um novo deployment chamado `web-003`;
    - Escalar o deployment para `3 replicas`;
    - Certifique-se de que o número desejado de pods esteja sempre em execução;
</details>

<details>
<summary>CKA Challenge Question 5</summary>

5. Question
    - Atualizar o Cluster (Masters e nodes) de `x.xx.x` para `x.xx.x`;
    - Certifique-se de que o número desejado do pod esteja sempre em execução
</details>

<details>
<summary>CKA Challenge Question 6</summary>

6. Question
    - Criar um pod chamado `web-load-5461` usando a imagem `nginx:1.17` com o `label` configurado para `tier=web`;
</details>

<details>
<summary>CKA Challenge Question 7</summary>

7. Question
    - Criar um multi container pod, `multi-pod` no namespace `desenvolvimento` usando as imagens `nginx` e `redis`;
</details>

<details>
<summary>CKA Challenge Question 8</summary>

8. Question
    - Criar um novo deployment chamado `nginx-deploy` com uma imagem `nginx:1.16` com `8 replicas`;
    - Certificque-se de que nenhum pod seja implantado em um nó de trabalho: `worker-node-1`;
    - [NOTA] - Reverter as alterações realizadas
    - [Laboratório - Challenge 8](./labs/lab-desafio-8.md)
</details>

<details>
<summary>CKA Challenge Question 9</summary>

9. Question
    - Criar um `ReplicaSet` (Nome: `web-pod`, Imagem `nginx:1.16` e `3 replicas`);
    - Já existe um pod em execução no cluster;
    - Certifique-se de que a contagem total do pod em execução em um cluster não seja superior a 3;
</details>

<details>
<summary>CKA Challenge Question 10</summary>

10. Question
    - Existem 3 nós no cluster, crie `DaemonSet` (Nome: my-pod, imagem nginx) em cada nó, exceto um (work-node-3)
</details>

<details>
<summary>CKA Challenge Question 11</summary>

11. Question

    - There are various pods running in all the namespaces of kubernetes cluster.  
    - Write a command into `/opt/pods_asc.sh` which list all the `Pods` sorted by the `AGE` in Ascending order.

    &nbsp;
    - Existem vários pods em execução em todos os namespaces do cluster Kubernetes. 
    - Escreva um comando em `/opt/pods_asc.sh` que liste todos os `Pods` classificados por idade em ordem crescente.

    &nbsp;
    - [Laboratório - Challenge 11](./labs/lab-desafio-11.md)
</details>

<details>
<summary>CKA Challenge Question 12</summary>

12. Question

    - Create a static pod on `k8s-lab-node-1` called `static-nginx` with image `nginx`;
    - You have to make sure that it is recreated/restarted automatically in case of any failure happens.

    &nbsp;
    - Crie um pod estático em `k8s-lab-node-1` chamado `static-nginx` com a imagem `nginx`;
    - Você deve ter certeza de que ele será recriado/reiniciado automaticamente no caso de ocorrer alguma falha.

    &nbsp;
    - [Laboratório - Challenge 12](./labs/lab-desafio-12.md)
</details>

<details>
<summary>CKA Challenge Question 13</summary>

13. Question

    - Create a pod called pod-multi with two containers, description mentioned below;
        - Container 1: name `container1`, image `nginx`;
        - Container 2: name `container2`, image `busybox`, command `sleep 4800`;
    
    &nbsp;
    - Crie um pod chamado pod-multi com dois containers, descrição mencionada abaixo;
        - Container 1: nome `container1`, imagem `nginx`;
        - Container 2: nome `container2`, imagem `busybox`, comando `sleep 4800`;

    &nbsp;
    - [Laboratório - Challenge 13](./labs/lab-desafio-13.md)
</details>

<details>
<summary>CKA Challenge Question 14</summary>

14. Question
    - Create a pod called `delta-pod` in defense namaspace belonging to the development environment `(env=dev)` and frontend tier `(tier=front)`
    - Image: `nginx:1.17`

    &nbsp;
    - Crie um pod chamado `delta-pod` no namaspace de defesa pertencente ao ambiente de desenvolvimento `(env=dev)` e à camada de frontend `(tier=front)`
    - Imagem: `nginx:1.17`

    &nbsp;
    - [Laboratório - Challenge 14](./labs/lab-desafio-14.md)
</details>

<details>
<summary>CKA Challenge Question 15</summary>

15. Question
    - Create a pod called `web-pod` using image `nginx`;
    - Expose it internally with a service called `web-pod-svc`.
    - Check that you are able to look up'the service and pod from within the cluster;
    - Use the image: `busybox:1.28` for dns lookup;
    - Record results in `/root/web-svc.svc` and `/root/web-pod.pod`;

    &nbsp;
    - Crie um pod chamado `web-pod` usando a imagem `nginx`;
    - Exponha-o internamente com um serviço chamado `web-pod-svc`.
    - Verifique se você consegue consultar o serviço e o pod dentro do cluster;
    - Use a imagem: `busybox:1.28` para pesquisa de DNS;
    - Registre os resultados em `/root/web-svc.svc` e `/root/web-pod.pod`;

    &nbsp;
    - [Laboratório - Challenge 15](./labs/lab-desafio-15.md)
</details>

<details>
<summary>CKA Challenge Question 16</summary>

16. Question
    - Use `JSON PATH` query to retrieve the osImages of all the nodes and store it in a file `allNodes_osImage_45CVB34Ji.txt` at root location;
    - Note: The osImages are under the nodeInfo section under status of each node;

    &nbsp;
    - Use a consulta `JSON PATH` para recuperar os osImages de todos os nós e armazená-los em um arquivo `allNodes_osImage_45CVB34Ji.txt` no local raiz;
    - Nota: Os osImages estão na seção nodeInfo no status de cada nó;

    &nbsp;
    - [Laboratório - Challenge 16](./labs/lab-desafio-16.md)
</details>

<details>
<summary>CKA Challenge Question 17</summary>

17. Question
    - Create a Persistent Volume with the given spscification.
        - Volume Name: `pv-rnd`;
        - Storage: `100Mi`;
        - Access modes: `ReadWriteMany`
        - Host Path: `/pv/host_data-rnd`

    &nbsp;
    - Crie um volume persistente com a especificação fornecida.
        - Nome do volume: `pv-rnd`;
        - Armazenamento: `100Mi`;
        - Modos de acesso: `ReadWriteMany`
        - Caminho do host: `/pv/host_data-rnd`

    &nbsp;
    - [Laboratório - Challenge 17](./labs/lab-desafio-17.md)
</details>

