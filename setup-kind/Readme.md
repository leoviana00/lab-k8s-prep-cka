## Setup Kind

- Instalação no Linux

```bash
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.14.0/kind-linux-amd64

chmod +x ./kind

sudo mv ./kind /usr/local/bin/kind
```

- Instalação no Windows

```bash
curl.exe -Lo kind-windows-amd64.exe https://kind.sigs.k8s.io/dl/v0.14.0/kind-windows-amd64

Move-Item .\kind-windows-amd64.exe c:\kind.exe
```

- Instalação no Windows via `Chocalaty`

```bash
choco install kind
```

- Criando um cluster

```bash
kind create cluster --name kind-cka --config ./setup-kind/kind-3-nodes.yaml
```

- Visualizar clusters

```bash
kind get clusters
```

- Visualizando nodes

```bash
kubectl get nodes
```

- Deletando Cluster

```bash
kind delete clusters
```

## Helm

- Install Helm Windows

```bash
choco install kubernetes-helm
```