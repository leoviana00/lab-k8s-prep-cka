## Join new node to existing cluster

- Adicionar mais nós de trabalho ao cluster Kubernetes usando a ferramenta de linha de comando kubeadm.
- OBS: Utilizando esse setup [Setup K8S Kubespray](../../setup-k8s-kubespray/kubespray/kubespray.md)

## Pré-requisitos

1. Você precisa ter um cluster Kubernetes funcionando – nó do plano de controle configurado e funcionando
2. Tempo de execução do contêiner ( Docker , cri-o ,containerd, etc) e ferramentas Kubernetes (kubeadm e kubelet) instaladas em seu nó Worker.
3. Se estiver usando um firewall como firewalld, as portas 10250 , 30000-32767 e as portas exigidas pelo complemento de rede do Pod devem ser abertas no firewall.
4. Acesso SSH à máquina a ser adicionada
5. Kubectl configurado para verificar se o nó está disponível em seu cluster

## Etapas

1. Obtenha o token de adesão
- Um token é necessário ao ingressar um novo nó de trabalho no cluster Kubernetes. Ao inicializar um cluster com kubeadm, é gerado um token que expira após 24 horas.
- Verifique se você possui um token – Execute o comando no nó Control:

```bash
kubeadm token list
```

- Se o token expirou, gere um novo com o comando:

```bash
kubeadm token create --print-join-command
```

2. Obter hash do certificado Discovery Token CA

- Para descoberta baseada em token, o comando join valida a chave pública da CA raiz combinando seu hash com aquele fornecido. Obtenha o hash do certificado CA do token de descoberta no nó de controle executando o comando abaixo.

```bash
openssl x509 -pubkey -in /etc/kubernetes/pki/ca.crt | openssl rsa -pubin -outform der 2>/dev/null | openssl dgst -sha256 -hex | sed 's/^.* //'
```

3. Obter o endereço de anúncio do servidor API

```bash
kubectl cluster-info
```

4. Ingressar no novo nó de trabalho do Kubernetes em um cluster
- O kubeadm joincomando é usado para inicializar um nó de trabalho do Kubernetes ou um nó de plano de controle adicional e juntá-lo ao cluster. A sintaxe de comando para ingressar um nó de trabalho no cluster é:

```bash
kubeadm join [api-server-endpoint] [flags]
```

```console
- --tokenstring: Token a ser usado
- --discovery-token-ca-cert-hash: Tem um formato: <tipo>:<valor>
```

- Portanto, nosso comando join completo terá o formato:

```bash
kubeadm join \
  <control-plane-host>:<control-plane-port> \
  --token <token> \
  --discovery-token-ca-cert-hash sha256:<hash>
```

- Exemplo:
```bash
sudo kubeadm join \
  192.168.122.195:6443 \
  --token nx1jjq.u42y27ip3bhmj8vj \
  --discovery-token-ca-cert-hash sha256:c6de85f6c862c0d58cc3d10fd199064ff25c4021b6e88475822d6163a25b4a6c
```

- Aguarde até que o nó tenha o status “ Pronto ” – Verifique o nó de controle

```bash
watch kubectl get nodes
```

## Removendo um nó de trabalho do cluster

- Para remover um nó do trabalhador Kubernetes do cluster, execute as operações a seguir.

1. Migrar pods do nó:

```bash
kubectl drain k8s-lab-node-2 --delete-emptydir-data --ignore-daemonsets --force
```

2. Impedir que um nó agende o uso de novos pods – Marcar o nó como não programável

```bash
kubectl cordon <node-name>
```

3. Reverter alterações feitas no nó por ' kubeadm join ' – Executar no nó de trabalho a ser removido

```bash
sudo kubeadm reset
```

- Você pode então refazer o mesmo processo de ingressar um novo nó no cluster assim que o comando kubeadm reset for executado com êxito.