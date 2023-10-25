## 🚀 Simulado

- Configuração do ambiente:
```bash
alias k=kubectl 
export do="--dry-run=client -o yaml"
export now="--force --grace-period 0"
```

- Para fazer o vim usar 2 espaços para uma edição da guia ~/.vimrc conter:
```bash
~/.vimrc
```
```console
set tabstop=2
set expandtab
set shiftwidth=2
```

## Questões

<details>
<summary>Question 1 | Contexts</summary>

1. Questão 1 do simulado
    - You have access to multiple clusters from your main terminal through kubectl contexts. Write all those context names into /opt/course/1/contexts.

    - Next write a command to display the current context into /opt/course/1/context_default_kubectl.sh, the command should use kubectl.

    - Finally write a second command doing the same thing into /opt/course/1/context_default_no_kubectl.sh, but without the use of kubectl.

    &nbsp;
    - Você tem acesso a vários clusters do seu terminal principal por meio de contextos kubectl. Escreva todos esses nomes de contexto em /opt/course/1/contexts.

    - Em seguida, escreva um comando para exibir o contexto atual em /opt/course/1/context_default_kubectl.sh, o comando deve usar kubectl.

    - Por fim, escreva um segundo comando fazendo a mesma coisa em /opt/course/1/context_default_no_kubectl.sh, mas sem o uso de kubectl.

    &nbsp;
    - [Laboratório - Questão 1](./solucao/question-1/Readme.md)
</details>

<details>
<summary>Question 2 | Schedule Pod on Master Node</summary>

2. Questão 2 do simulado
    - Use context: kubectl config use-context k8s-c1-H

    - Create a single Pod of image httpd:2.4.41-alpine in Namespace default. The Pod should be named pod1 and the container should be named pod1-container. This Pod should only be scheduled on a controlplane node, do not add new labels any nodes.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c1-H

    - Crie um único pod de imagem httpd:2.4.41-alpine no Namespace padrão. O pod deve ser denominado pod1 e o contêiner deve ser denominado pod1-container. Este pod só deve ser agendado em um nó do plano de controle, não adicione novos rótulos em nenhum nó.

    &nbsp;
    - [Laboratório - Questão 2](./solucao/question-2/Readme.md)
</details>

<details>
<summary>Question 3 | Scale down StatefulSet</summary>

3. Questão 3 do simulado
    - Use context: kubectl config use-context k8s-c1-H

    - There are two Pods named o3db-* in Namespace project-c13. C13 management asked you to scale the Pods down to one replica to save resources.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c1-H

    - Existem dois pods chamados o3db-* no Namespace project-c13. O gerenciamento C13 solicitou que você reduzisse os pods para uma réplica para economizar recursos.

    &nbsp;
    - [Laboratório - Questão 3](./solucao/question-3/Readme.md)
</details>

<details>
<summary>Question 4 | Pod Ready if Service is reachable</summary>

4. Questão template do simulado
    - Use context: kubectl config use-context k8s-c1-H

    - Do the following in Namespace default. Create a single Pod named ready-if-service-ready of image nginx:1.16.1-alpine. Configure a LivenessProbe which simply executes command true. Also configure a ReadinessProbe which does check if the url http://service-am-i-ready:80 is reachable, you can use wget -T2 -O- http://service-am-i-ready:80 for this. Start the Pod and confirm it isn't ready because of the ReadinessProbe.

    - Create a second Pod named am-i-ready of image nginx:1.16.1-alpine with label id: cross-server-ready. The already existing Service service-am-i-ready should now have that second Pod as endpoint.

    - Now the first Pod should be in ready state, confirm that.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c1-H

    - Faça o seguinte no Namespace padrão. Crie um único pod chamado ready-if-service-ready da imagem nginx:1.16.1-alpine. Configure um LivenessProbe que simplesmente executa o comando true. Configure também um ReadinessProbe que verifica se o URL http://service-am-i-ready:80 está acessível, você pode usar wget -T2 -O- http://service-am-i-ready:80 para isso . Inicie o pod e confirme se ele não está pronto por causa do ReadinessProbe.

    - Crie um segundo pod chamado am-i-ready da imagem nginx:1.16.1-alpine com o rótulo id: cross-server-ready. O serviço já existente service-am-i-ready agora deve ter esse segundo pod como endpoint.

    - Agora o primeiro Pod deve estar pronto, confirme.

    &nbsp;
    - [Laboratório - Questão 4](./solucao/question-4/Readme.md)
</details>

<details>
<summary>Question 5 | Kubectl sorting</summary>

5. Questão template do simulado
    - Use context: kubectl config use-context k8s-c1-H

    - There are various Pods in all namespaces. Write a command into /opt/course/5/find_pods.sh which lists all Pods sorted by their AGE (metadata.creationTimestamp).

    - Write a second command into /opt/course/5/find_pods_uid.sh which lists all Pods sorted by field metadata.uid. Use kubectl sorting for both commands.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c1-H

    - Existem vários Pods em todos os namespaces. Escreva um comando em /opt/course/5/find_pods.sh que lista todos os pods classificados por IDADE (metadata.creationTimestamp).

    - Escreva um segundo comando em /opt/course/5/find_pods_uid.sh que lista todos os Pods classificados pelo campo metadata.uid. Use a classificação kubectl para ambos os comandos.

    &nbsp;
    - [Laboratório - Questão 5](./solucao/question-5/Readme.md)
</details>

<details>
<summary>Question 6 | Storage, PV, PVC, Pod volume</summary>

6. Questão 6 do simulado
    - Use context: kubectl config use-context k8s-c1-H

    - Create a new PersistentVolume named safari-pv. It should have a capacity of 2Gi, accessMode ReadWriteOnce, hostPath /Volumes/Data and no storageClassName defined.

    - Next create a new PersistentVolumeClaim in Namespace project-tiger named safari-pvc . It should request 2Gi storage, accessMode ReadWriteOnce and should not define a storageClassName. The PVC should bound to the PV correctly.

    - Finally create a new Deployment safari in Namespace project-tiger which mounts that volume at /tmp/safari-data. The Pods of that Deployment should be of image httpd:2.4.41-alpine.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c1-H

    - Crie um novo PersistentVolume chamado safari-pv. Deve ter capacidade de 2Gi, accessMode ReadWriteOnce, hostPath /Volumes/Data e nenhum storageClassName definido.

    - Em seguida, crie um novo PersistentVolumeClaim no Namespace project-tiger chamado safari-pvc . Deve solicitar armazenamento 2Gi, accessMode ReadWriteOnce e não deve definir um storageClassName. O PVC deve estar ligado ao PV corretamente.

    - Por fim, crie um novo safari de implantação no namespace project-tiger que monta esse volume em /tmp/safari-data. Os pods dessa implantação devem ter a imagem httpd:2.4.41-alpine.

    &nbsp;
    - [Laboratório - Questão 6](./solucao/question-6/Readme.md)
</details>

<details>
<summary>Question 7 | Node and Pod Resource Usage</summary>

7. Questão 7 do simulado
    - Use context: kubectl config use-context k8s-c1-H

    - The metrics-server has been installed in the cluster. Your college would like to know the kubectl commands to:

    1. show Nodes resource usage;
    2. show Pods and their containers resource usage;

    - Please write the commands into /opt/course/7/node.sh and /opt/course/7/pod.sh.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c1-H

    - O servidor de métricas foi instalado no cluster. Sua faculdade gostaria de saber os comandos do kubectl para:

    1. mostrar o uso de recursos dos nós;
    2. mostrar o uso de recursos dos pods e seus contêineres;

    - Por favor, escreva os comandos em /opt/course/7/node.sh e /opt/course/7/pod.sh.

    &nbsp;
    - [Laboratório - Questão 7](./solucao/question-7/Readme.md)
</details>

<details>
<summary>Question 8 | Get Master Information</summary>

8. Questão 8 do simulado
    - Use context: kubectl config use-context k8s-c1-H

    - Ssh into the controlplane node with ssh cluster1-controlplane1. Check how the controlplane components kubelet, kube-apiserver, kube-scheduler, kube-controller-manager and etcd are started/installed on the controlplane node. Also find out the name of the DNS application and how it's started/installed on the controlplane node.

    - Write your findings into file /opt/course/8/controlplane-components.txt. The file should be structured like:

    - `/opt/course/8/controlplane-components.txt`:
    ```bash
    kubelet: [TYPE]
    kube-apiserver: [TYPE]
    kube-scheduler: [TYPE]
    kube-controller-manager: [TYPE]
    etcd: [TYPE]
    dns: [TYPE] [NAME]
    ```
    - Choices of [TYPE] are: not-installed, process, static-pod, pod
    

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c1-H

    - Ssh no nó do plano de controle com ssh cluster1-controlplane1. Verifique como os componentes do plano de controle kubelet, kube-apiserver, kube-scheduler, kube-controller-manager e etcd são iniciados/instalados no nó do plano de controle. Descubra também o nome do aplicativo DNS e como ele é iniciado/instalado no nó do plano de controle.

    - Escreva suas descobertas no arquivo /opt/course/8/controlplane-components.txt. O arquivo deve ser estruturado como:

    - `/opt/course/8/controlplane-components.txt`:
    ```bash
    kubelet: [TIPO]
    kube-apiserver: [TIPO]
    agendador kube: [TIPO]
    kube-controller-manager: [TIPO]
    etcd: [TIPO]
    DNS: [TIPO] [NOME]
    ```
    - As opções de [TIPO] são: não instalado, processo, pod estático, pod

    &nbsp;
    - [Laboratório - Questão 8](./solucao)
</details>

<details>
<summary>Question 9 | Kill Scheduler, Manual Scheduling</summary>

9. Questão 9 do simulado
    - Use context: kubectl config use-context k8s-c2-AC

    - Ssh into the controlplane node with ssh cluster2-controlplane1. Temporarily stop the kube-scheduler, this means in a way that you can start it again afterwards.

    - Create a single Pod named manual-schedule of image httpd:2.4-alpine, confirm it's created but not scheduled on any node.

    - Now you're the scheduler and have all its power, manually schedule that Pod on node cluster2-controlplane1. Make sure it's running.

    - Start the kube-scheduler again and confirm it's running correctly by creating a second Pod named manual-schedule2 of image httpd:2.4-alpine and check if it's running on cluster2-node1.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c2-AC

    - Ssh no nó do plano de controle com ssh cluster2-controlplane1. Pare temporariamente o kube-scheduler, isso significa que você poderá iniciá-lo novamente depois.

    - Crie um único pod chamado manual-schedule da imagem httpd:2.4-alpine, confirme se ele foi criado, mas não programado em nenhum nó.

    - Agora você é o agendador e tem todo o poder, agende manualmente esse Pod no nó cluster2-controlplane1. Certifique-se de que esteja funcionando.

    - Inicie o kube-scheduler novamente e confirme se ele está funcionando corretamente criando um segundo pod chamado manual-schedule2 da imagem httpd:2.4-alpine e verifique se ele está sendo executado no cluster2-node1.

    &nbsp;
    - [Laboratório - Questão 9](./solucao)
</details>

<details>
<summary>Question 10 | RBAC ServiceAccount Role RoleBinding</summary>

10. Questão 10 do simulado
    - Use context: kubectl config use-context k8s-c1-H

    - Create a new ServiceAccount processor in Namespace project-hamster. Create a Role and RoleBinding, both named processor as well. These should allow the new SA to only create Secrets and ConfigMaps in that Namespace.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c1-H

    - Crie um novo processador ServiceAccount no namespace project-hamster. Crie um Role e RoleBinding, ambos nomeados como processador também. Isso deve permitir que o novo SA crie apenas segredos e ConfigMaps nesse namespace.

    &nbsp;
    - [Laboratório - Questão 10](./solucao)
</details>

<details>
<summary>Question 11 | DaemonSet on all Nodes</summary>

11. Questão 11 do simulado
    - Use context: kubectl config use-context k8s-c1-H

    - Use Namespace project-tiger for the following. Create a DaemonSet named ds-important with image httpd:2.4-alpine and labels id=ds-important and uuid=18426a0b-5f59-4e10-923f-c0e078e82462. The Pods it creates should request 10 millicore cpu and 10 mebibyte memory. The Pods of that DaemonSet should run on all nodes, also controlplanes.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c1-H

    - Use Namespace project-tiger para o seguinte. Crie um DaemonSet chamado ds-important com imagem httpd:2.4-alpine e rótulos id=ds-important e uuid=18426a0b-5f59-4e10-923f-c0e078e82462. Os pods criados devem solicitar CPU de 10 milicore e memória de 10 mebibytes. Os pods desse DaemonSet devem ser executados em todos os nós, também nos planos de controle.

    &nbsp;
    - [Laboratório - Questão 11](./solucao)
</details>

<details>
<summary>Question 12 | Deployment on all Nodes</summary>

12. Questão 12 do simulado
    - Use context: kubectl config use-context k8s-c1-H

    - Use Namespace project-tiger for the following. Create a Deployment named deploy-important with label id=very-important (the Pods should also have this label) and 3 replicas. It should contain two containers, the first named container1 with image nginx:1.17.6-alpine and the second one named container2 with image kubernetes/pause.

    - There should be only ever one Pod of that Deployment running on one worker node. We have two worker nodes: cluster1-node1 and cluster1-node2. Because the Deployment has three replicas the result should be that on both nodes one Pod is running. The third Pod won't be scheduled, unless a new worker node will be added.

    - In a way we kind of simulate the behaviour of a DaemonSet here, but using a Deployment and a fixed number of replicas.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c1-H

    - Use Namespace project-tiger para o seguinte. Crie uma implantação chamada deploy-important com rótulo id=very-important (os pods também devem ter esse rótulo) e 3 réplicas. Ele deve conter dois contêineres, o primeiro denominado container1 com imagem nginx:1.17.6-alpine e o segundo denominado container2 com imagem kubernetes/pause.

    - Deve haver apenas um pod dessa implantação em execução em um nó de trabalho. Temos dois nós de trabalho: cluster1-node1 e cluster1-node2. Como a implantação tem três réplicas, o resultado deve ser que em ambos os nós um pod esteja em execução. O terceiro pod não será agendado, a menos que um novo nó de trabalho seja adicionado.

    - De certa forma simulamos aqui o comportamento de um DaemonSet, mas usando um Deployment e um número fixo de réplicas.

    &nbsp;
    - [Laboratório - Questão 12](./solucao)
</details>

<details>
<summary>Question 13 | Multi Containers and Pod shared Volume</summary>

13. Questão 13 do simulado
    - Use context: kubectl config use-context k8s-c1-H

    - Create a Pod named multi-container-playground in Namespace default with three containers, named c1, c2 and c3. There should be a volume attached to that Pod and mounted into every container, but the volume shouldn't be persisted or shared with other Pods.

    - Container c1 should be of image nginx:1.17.6-alpine and have the name of the node where its Pod is running available as environment variable MY_NODE_NAME.

    - Container c2 should be of image busybox:1.31.1 and write the output of the date command every second in the shared volume into file date.log. You can use while true; do date >> /your/vol/path/date.log; sleep 1; done for this.

    - Container c3 should be of image busybox:1.31.1 and constantly send the content of file date.log from the shared volume to stdout. You can use tail -f /your/vol/path/date.log for this.

    - Check the logs of container c3 to confirm correct setup.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c1-H

    - Crie um pod denominado multi-container-playground no Namespace padrão com três contêineres, denominados c1, c2 e c3. Deve haver um volume anexado a esse pod e montado em cada contêiner, mas o volume não deve ser persistido ou compartilhado com outros pods.

    - O container c1 deve ter a imagem nginx:1.17.6-alpine e ter o nome do nó onde seu Pod está rodando disponível como variável de ambiente MY_NODE_NAME.

    - O contêiner c2 deve ter a imagem busybox:1.31.1 e gravar a saída do comando date a cada segundo no volume compartilhado no arquivo date.log. Você pode usar enquanto verdadeiro; faça data >> /your/vol/path/date.log; dormir 1; feito para isso.

    - O container c3 deve ter a imagem busybox:1.31.1 e enviar constantemente o conteúdo do arquivo date.log do volume compartilhado para stdout. Você pode usar tail -f /your/vol/path/date.log para isso.

    - Verifique os logs do contêiner c3 para confirmar a configuração correta.

    &nbsp;
    - [Laboratório - Questão 13](./solucao)
</details>

<details>
<summary>Question 14 | Find out Cluster Information</summary>

14. Questão 14 do simulado
    - Use context: kubectl config use-context k8s-c1-H

    - You're ask to find out following information about the cluster k8s-c1-H :

    1. How many controlplane nodes are available?
    2. How many worker nodes are available?
    3. What is the Service CIDR?
    4. Which Networking (or CNI Plugin) is configured and where is its config file?
    5. Which suffix will static pods have that run on cluster1-node1?
    6. Write your answers into file /opt/course/14/cluster-info, structured like this:

    - `/opt/course/14/cluster-info`
    ```bash
    1: [ANSWER]
    2: [ANSWER]
    3: [ANSWER]
    4: [ANSWER]
    5: [ANSWER]
    ```

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c1-H

    - Você deve descobrir as seguintes informações sobre o cluster k8s-c1-H:

    1. Quantos nós do plano de controle estão disponíveis?
    2. Quantos nós de trabalho estão disponíveis?
    3. O que é o CIDR de Serviço?
    4. Qual rede (ou plug-in CNI) está configurada e onde está seu arquivo de configuração?
    5. Qual sufixo os pods estáticos terão para execução em cluster1-node1?
    6. Escreva suas respostas no arquivo /opt/course/14/cluster-info, estruturado assim:

    - `/opt/course/14/cluster-info`
    ```bash
    1: [RESPOSTA]
    2: [RESPOSTA]
    3: [RESPOSTA]
    4: [RESPOSTA]
    5: [RESPOSTA]
    ```

    &nbsp;
    - [Laboratório - Questão 14](./solucao)
</details>

<details>
<summary>Question 15 | Cluster Event Logging</summary>

15. Questão 15 do simulado
    - Use context: kubectl config use-context k8s-c2-AC

    - Write a command into /opt/course/15/cluster_events.sh which shows the latest events in the whole cluster, ordered by time (metadata.creationTimestamp). Use kubectl for it.

    - Now kill the kube-proxy Pod running on node cluster2-node1 and write the events this caused into /opt/course/15/pod_kill.log.

    - Finally kill the containerd container of the kube-proxy Pod on node cluster2-node1 and write the events into /opt/course/15/container_kill.log.

    - Do you notice differences in the events both actions caused?

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c2-AC

    - Escreva um comando em /opt/course/15/cluster_events.sh que mostre os eventos mais recentes em todo o cluster, ordenados por hora (metadata.creationTimestamp). Use kubectl para isso.

    - Agora elimine o pod kube-proxy em execução no nó cluster2-node1 e grave os eventos que isso causou em /opt/course/15/pod_kill.log.

    - Por fim, elimine o contêiner containerd do pod kube-proxy no nó cluster2-node1 e grave os eventos em /opt/course/15/container_kill.log.

    - Você percebe diferenças nos eventos que ambas as ações causaram?

    &nbsp;
    - [Laboratório - Questão 15](./solucao)
</details>

<details>
<summary>Question 16 | Namespaces and Api Resources</summary>

16. Questão 16 do simulado
    - Use context: kubectl config use-context k8s-c1-H

    - Write the names of all namespaced Kubernetes resources (like Pod, Secret, ConfigMap...) into /opt/course/16/resources.txt.

    - Find the project-* Namespace with the highest number of Roles defined in it and write its name and amount of Roles into /opt/course/16/crowded-namespace.txt.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c1-H

    - Escreva os nomes de todos os recursos do Kubernetes com namespace (como Pod, Secret, ConfigMap...) em /opt/course/16/resources.txt.

    - Encontre o namespace do projeto-* com o maior número de funções definidas nele e escreva seu nome e quantidade de funções em /opt/course/16/crowded-namespace.txt.

    &nbsp;
    - [Laboratório - Questão 16](./solucao)
</details>

<details>
<summary>Question 17 | Find Container of Pod and check info</summary>

17. Questão 17 do simulado
    - Use context: kubectl config use-context k8s-c1-H

    - In Namespace project-tiger create a Pod named tigers-reunite of image httpd:2.4.41-alpine with labels pod=container and container=pod. Find out on which node the Pod is scheduled. Ssh into that node and find the containerd container belonging to that Pod.

    - Using command crictl:

    - Write the ID of the container and the info.runtimeType into /opt/course/17/pod-container.txt

    - Write the logs of the container into /opt/course/17/pod-container.log

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c1-H

    - No Namespace project-tiger crie um Pod chamado Tigers-reunite da imagem httpd:2.4.41-alpine com os rótulos pod=container e container=pod. Descubra em qual nó o pod está programado. Faça Ssh nesse nó e encontre o contêiner containerd pertencente a esse pod.

    - Usando o comando crictl:

    - Escreva o ID do contêiner e o info.runtimeType em /opt/course/17/pod-container.txt

    - Escreva os logs do contêiner em /opt/course/17/pod-container.log

    &nbsp;
    - [Laboratório - Questão 17](./solucao)
</details>

<details>
<summary>Question 18 | Fix Kubelet</summary>

18. Questão 18 do simulado
    - Use context: kubectl config use-context k8s-c3-CCC

    - There seems to be an issue with the kubelet not running on cluster3-node1. Fix it and confirm that cluster has node cluster3-node1 available in Ready state afterwards. You should be able to schedule a Pod on cluster3-node1 afterwards.

    - Write the reason of the issue into /opt/course/18/reason.txt.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c3-CCC

    - Parece haver um problema com o kubelet não sendo executado no cluster3-node1. Corrija-o e confirme se o cluster tem o nó cluster3-node1 disponível no estado Pronto posteriormente. Você poderá agendar um pod no cluster3-node1 posteriormente.

    - Escreva o motivo do problema em /opt/course/18/reason.txt

    &nbsp;
    - [Laboratório - Questão 18](./solucao)
</details>

<details>
<summary>Question 19 | Create Secret and mount into Pod</summary>

1. Questão 19 do simulado
    - `NOTE`: This task can only be solved if questions 18 or 20 have been successfully implemented and the k8s-c3-CCC cluster has a functioning worker node

    - Use context: kubectl config use-context k8s-c3-CCC

    - Do the following in a new Namespace secret. Create a Pod named secret-pod of image busybox:1.31.1 which should keep running for some time.

    - There is an existing Secret located at /opt/course/19/secret1.yaml, create it in the Namespace secret and mount it readonly into the Pod at /tmp/secret1.

    - Create a new Secret in Namespace secret called secret2 which should contain user=user1 and pass=1234. These entries should be available inside the Pod's container as environment variables APP_USER and APP_PASS.

    - Confirm everything is working.

    &nbsp;
    - `NOTA`: Esta tarefa só pode ser resolvida se as questões 18 ou 20 tiverem sido implementadas com sucesso e o cluster k8s-c3-CCC tiver um nó de trabalho funcional

    - Usar contexto: kubectl config use-context k8s-c3-CCC

    - Faça o seguinte em um novo segredo do Namespace. Crie um pod chamado secret-pod da imagem busybox:1.31.1 que deve continuar em execução por algum tempo.

    - Existe um segredo existente localizado em /opt/course/19/secret1.yaml, crie-o no segredo do namespace e monte-o somente leitura no pod em /tmp/secret1.

    - Crie um novo segredo no namespace secreto chamado secret2 que deve conter user=user1 e pass=1234. Essas entradas devem estar disponíveis no contêiner do pod como variáveis ​​de ambiente APP_USER e APP_PASS.

    - Confirme que tudo está funcionando.

    &nbsp;
    - [Laboratório - Questão 19](./solucao)
</details>

<details>
<summary>Question 20 | Update Kubernetes Version and join cluster</summary>

20. Questão 20 do simulado
    - Use context: kubectl config use-context k8s-c3-CCC

    - Your coworker said node cluster3-node2 is running an older Kubernetes version and is not even part of the cluster. Update Kubernetes on that node to the exact version that's running on cluster3-controlplane1. Then add this node to the cluster. Use kubeadm for this.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c3-CCC

    - Seu colega de trabalho disse que o nó cluster3-node2 está executando uma versão mais antiga do Kubernetes e nem faz parte do cluster. Atualize o Kubernetes nesse nó para a versão exata que está em execução no cluster3-controlplane1. Em seguida, adicione este nó ao cluster. Use kubeadm para isso.

    &nbsp;
    - [Laboratório - Questão 20](./solucao)
</details>

<details>
<summary>Question 21 | Create a Static Pod and Service</summary>

21. Questão 21 do simulado
    - Use context: kubectl config use-context k8s-c3-CCC

    - Create a Static Pod named my-static-pod in Namespace default on cluster3-controlplane1. It should be of image nginx:1.16-alpine and have resource requests for 10m CPU and 20Mi memory.

    - Then create a NodePort Service named static-pod-service which exposes that static Pod on port 80 and check if it has Endpoints and if it's reachable through the cluster3-controlplane1 internal IP address. You can connect to the internal node IPs from your main terminal.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c3-CCC

    - Crie um pod estático chamado my-static-pod no Namespace padrão em cluster3-controlplane1. Deve ter a imagem nginx:1.16-alpine e ter solicitações de recursos para 10m de CPU e 20Mi de memória.

    - Em seguida, crie um serviço NodePort chamado static-pod-service que expõe esse Pod estático na porta 80 e verifique se ele possui Endpoints e se é acessível através do endereço IP interno cluster3-controlplane1. Você pode se conectar aos IPs dos nós internos a partir do seu terminal principal.

    &nbsp;
    - [Laboratório - Questão 21](./solucao)
</details>

<details>
<summary>Question 22 | Check how long certificates are valid</summary>

22. Questão 22 do simulado
    - Use context: kubectl config use-context k8s-c2-AC

    - Check how long the kube-apiserver server certificate is valid on cluster2-controlplane1. Do this with openssl or cfssl. Write the exipiration date into /opt/course/22/expiration.

    - Also run the correct kubeadm command to list the expiration dates and confirm both methods show the same date.

    - Write the correct kubeadm command that would renew the apiserver server certificate into /opt/course/22/kubeadm-renew-certs.sh.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c2-AC

    - Verifique por quanto tempo o certificado do servidor kube-apiserver é válido no cluster2-controlplane1. Faça isso com openssl ou cfssl. Escreva a data de validade em /opt/course/22/expiration.

    - Execute também o comando kubeadm correto para listar as datas de expiração e confirmar se ambos os métodos mostram a mesma data.

    - Escreva o comando kubeadm correto que renovaria o certificado do servidor apiserver em /opt/course/22/kubeadm-renew-certs.sh.

    &nbsp;
    - [Laboratório - Questão 22](./solucao)
</details>

<details>
<summary>Question 23 | Kubelet client/server cert info</summary>

23. Questão 23 do simulado
    - Use context: kubectl config use-context k8s-c2-AC

    - Node cluster2-node1 has been added to the cluster using kubeadm and TLS bootstrapping.

    - Find the "Issuer" and "Extended Key Usage" values of the cluster2-node1:

    1. kubelet client certificate, the one used for outgoing connections to the kube-apiserver.
    2. kubelet server certificate, the one used for incoming connections from the kube-apiserver.

    - Write the information into file /opt/course/23/certificate-info.txt.

    - Compare the "Issuer" and "Extended Key Usage" fields of both certificates and make sense of these.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c2-AC

    - O nó cluster2-node1 foi adicionado ao cluster usando kubeadm e inicialização TLS.

    - Encontre os valores "Issuer" e "Extended Key Usage" do cluster2-node1:

    1. certificado de cliente kubelet, aquele usado para conexões de saída com o kube-apiserver.
    2. certificado do servidor kubelet, aquele usado para conexões de entrada do kube-apiserver.

    - Escreva as informações no arquivo /opt/course/23/certificate-info.txt.

    - Compare os campos "Emissor" e "Uso de chave estendida" de ambos os certificados e entenda-os.

    &nbsp;
    - [Laboratório - Questão 23](./solucao)
</details>

<details>
<summary>Question 24 | NetworkPolicy</summary>

24. Questão 24 do simulado
    - Use context: kubectl config use-context k8s-c1-H

    - There was a security incident where an intruder was able to access the whole cluster from a single hacked backend Pod.

    - To prevent this create a NetworkPolicy called np-backend in Namespace project-snake. It should allow the backend-* Pods only to:

    1. connect to db1-* Pods on port 1111
    2. connect to db2-* Pods on port 2222

    - Use the app label of Pods in your policy.

    - After implementation, connections from backend-* Pods to vault-* Pods on port 3333 should for example no longer work.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c1-H

    - Houve um incidente de segurança em que um invasor conseguiu acessar todo o cluster a partir de um único pod de back-end hackeado.

    - Para evitar isso, crie uma NetworkPolicy chamada np-backend no Namespace project-snake. Deve permitir que os pods backend-* apenas:

    1. conecte-se aos pods db1-* na porta 1111
    2. conecte-se aos pods db2-* na porta 2222

    - Use o rótulo do aplicativo Pods na sua política.

    - Após a implementação, as conexões dos pods backend-* aos pods vault-* na porta 3333, por exemplo, não deverão mais funcionar.

    &nbsp;
    - [Laboratório - Questão 24](./solucao)
</details>

<details>
<summary>Question 25 | Etcd Snapshot Save and Restore</summary>

25. Questão 25 do simulado
    - Use context: kubectl config use-context k8s-c3-CCC

    - Make a backup of etcd running on cluster3-controlplane1 and save it on the controlplane node at /tmp/etcd-backup.db.

    - Then create a Pod of your kind in the cluster.

    - Finally restore the backup, confirm the cluster is still working and that the created Pod is no longer with us.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c3-CCC

    - Faça um backup do etcd em execução no cluster3-controlplane1 e salve-o no nó do controlplane em /tmp/etcd-backup.db.

    - Em seguida, crie um Pod do seu tipo no cluster.

    - Por fim, restaure o backup, confirme se o cluster ainda está funcionando e se o Pod criado não está mais conosco.

    &nbsp;
    - [Laboratório - Questão 25](./solucao)
</details>

<details>
<summary>Extra Question 1 | Find Pods first to be terminated</summary>

26. Questão extra 1 do simulado
    - Use context: kubectl config use-context k8s-c1-H

    - Check all available Pods in the Namespace project-c13 and find the names of those that would probably be terminated first if the Nodes run out of resources (cpu or memory) to schedule all Pods. Write the Pod names into /opt/course/e1/pods-not-stable.txt.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c1-H

    - Verifique todos os Pods disponíveis no Namespace project-c13 e encontre os nomes daqueles que provavelmente seriam encerrados primeiro caso os Nodes ficassem sem recursos (cpu ou memória) para agendar todos os Pods. Escreva os nomes dos pods em /opt/course/e1/pods-not-stable.txt.

    &nbsp;
    - [Laboratório - Questão extra 1](./solucao)
</details>

<details>
<summary>Extra Question 2 | Curl Manually Contact API</summary>

27. Questão extra 2 do simulado
    - Use context: kubectl config use-context k8s-c1-H

    - There is an existing ServiceAccount secret-reader in Namespace project-hamster. Create a Pod of image curlimages/curl:7.65.3 named tmp-api-contact which uses this ServiceAccount. Make sure the container keeps running.

    - Exec into the Pod and use curl to access the Kubernetes Api of that cluster manually, listing all available secrets. You can ignore insecure https connection. Write the command(s) for this into file /opt/course/e4/list-secrets.sh.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c1-H

    - Existe um leitor secreto ServiceAccount existente no namespace project-hamster. Crie um pod de imagem curlimages/curl:7.65.3 chamado tmp-api-contact que usa esta ServiceAccount. Certifique-se de que o contêiner continue funcionando.

    - Execute no Pod e use curl para acessar manualmente a API Kubernetes desse cluster, listando todos os segredos disponíveis. Você pode ignorar a conexão https insegura. Escreva o(s) comando(s) para isso no arquivo /opt/course/e4/list-secrets.sh.

    &nbsp;
    - [Laboratório - Questão extra 2](./solucao)
</details>

<details>
<summary>Preview Question 1</summary>

28. Preview Question 1
    - Use context: kubectl config use-context k8s-c2-AC

    - The cluster admin asked you to find out the following information about etcd running on cluster2-controlplane1:

        - Server private key location
        - Server certificate expiration date
        - Is client certificate authentication enabled
    - Write these information into /opt/course/p1/etcd-info.txt

    - Finally you're asked to save an etcd snapshot at /etc/etcd-snapshot.db on cluster2-controlplane1 and display its status.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c2-AC

    - O administrador do cluster solicitou que você descobrisse as seguintes informações sobre o etcd em execução no cluster2-controlplane1:

        - Localização da chave privada do servidor
        - Data de expiração do certificado do servidor
        - A autenticação de certificado de cliente está habilitada?
    - Escreva essas informações em /opt/course/p1/etcd-info.txt

    - Finalmente, você será solicitado a salvar um instantâneo do etcd em /etc/etcd-snapshot.db no cluster2-controlplane1 e exibir seu status.


    &nbsp;
    - [Laboratório - Preview Question 1](./solucao)
</details>

<details>
<summary>Preview Question 2</summary>

29. Preview Question 2
    - Use context: kubectl config use-context k8s-c1-H

    - You're asked to confirm that kube-proxy is running correctly on all nodes. For this perform the following in Namespace project-hamster:

    - Create a new Pod named p2-pod with two containers, one of image nginx:1.21.3-alpine and one of image busybox:1.31. Make sure the busybox container keeps running for some time.

    - Create a new Service named p2-service which exposes that Pod internally in the cluster on port 3000->80.

    - Find the kube-proxy container on all nodes cluster1-controlplane1, cluster1-node1 and cluster1-node2 and make sure that it's using iptables. Use command crictl for this.

    - Write the iptables rules of all nodes belonging the created Service p2-service into file /opt/course/p2/iptables.txt.

    - Finally delete the Service and confirm that the iptables rules are gone from all nodes.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c1-H

    - Você será solicitado a confirmar se o kube-proxy está sendo executado corretamente em todos os nós. Para isso execute o seguinte no Namespace project-hamster:

    - Crie um novo Pod chamado p2-pod com dois contêineres, um de imagem nginx:1.21.3-alpine e outro de imagem busybox:1.31. Certifique-se de que o contêiner do busybox continue funcionando por algum tempo.

    - Crie um novo serviço chamado p2-service que expõe esse Pod internamente no cluster na porta 3000->80.

    - Encontre o contêiner kube-proxy em todos os nós cluster1-controlplane1, cluster1-node1 e cluster1-node2 e certifique-se de que ele esteja usando iptables. Use o comando crictl para isso.

    - Escreva as regras de iptables de todos os nós pertencentes ao serviço p2-service criado no arquivo /opt/course/p2/iptables.txt.

    - Por fim, exclua o Serviço e confirme se as regras do iptables desapareceram de todos os nós.

    &nbsp;
    - [Laboratório - Preview Question 2](./solucao)
</details>

<details>
<summary>Preview Question 3</summary>

30. Preview Question 3
    - Use context: kubectl config use-context k8s-c2-AC

    - Create a Pod named check-ip in Namespace default using image httpd:2.4.41-alpine. Expose it on port 80 as a ClusterIP Service named check-ip-service. Remember/output the IP of that Service.

    - Change the Service CIDR to 11.96.0.0/12 for the cluster.

    - Then create a second Service named check-ip-service2 pointing to the same Pod to check if your settings did take effect. Finally check if the IP of the first Service has changed.

    &nbsp;
    - Usar contexto: kubectl config use-context k8s-c2-AC

    - Crie um pod chamado check-ip no Namespace padrão usando a imagem httpd:2.4.41-alpine. Exponha-o na porta 80 como um serviço ClusterIP denominado check-ip-service. Lembre-se/exiba o IP desse serviço.

    - Altere o CIDR de serviço para 11.96.0.0/12 para o cluster.

    - Em seguida, crie um segundo serviço chamado check-ip-service2 apontando para o mesmo pod para verificar se suas configurações entraram em vigor. Por fim verifique se o IP do primeiro Serviço mudou.

    &nbsp;
    - [Laboratório - Preview Question 3](./solucao)
</details>

## Cenários

- [Cenários no Medium](https://levelup.gitconnected.com/kubernetes-cka-example-questions-practical-challenge-86318d85b4d)

<!-- <details>
<summary>Template</summary>

1. Questão template do simulado
    - 

    &nbsp;
    - 

    &nbsp;
    - [Laboratório - Questão template](./solucao)
</details> -->