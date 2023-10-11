<h1 align="center">Kubernetes - CKA</h1>

<p align="center">
  <img alt="Kubernetes" src="https://img.shields.io/static/v1?label=Kubernetes&message=CKA&color=8257E5&labelColor=000000"  />
  <img alt="License" src="https://img.shields.io/static/v1?label=license&message=MIT&color=49AA26&labelColor=000000">
</p>

<p align="center">
  <a href="#-projeto">Projeto</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-roadmap">Roadmap</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-ambiente">Ambiente</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-requisitos-computacionais">Requisitos Computacionais</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-roteiro-de-preparação-da-cka">Roteiro da CKA</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-desafios">Desafios</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-referências">Referências</a>
</p>

<p align="center">
  <img alt="Istio" src="data/cert.png">
</p>

## 💡 Projeto

- Preparar um cluster para iniciar os estudos sobre Kubernetes, e ao mesmo tempo abordar itens que são cobrados na certificação CKA.

## 👣 Roadmap 

- [x] Preparação de um cluster mínimo viável
- [x] Instalação através da ferramenta kubeadm
- [x] Prepara uma infraestrutura local através do uso de máquinas virtuais com VirtualBox e Vagrant
- [x] Utiliza o kubeadm para preparar um cluster kubernetes em uma determinada versão
- [x] Atualização do cluster para versão mais atualizada até o momento
- [x] Preparanção de um setup kubernetes com kubespray
- [x] Preparação de um setup kubernetes com kind
- [x] Lista de exercicios / Laboratórios

## ✨ Ambiente

- Setup Kubernetes com `Kubeadm`

1. [Virtualbox](https://www.virtualbox.org/wiki/Downloads)
2. [Vagrant](https://developer.hashicorp.com/vagrant/downloads)
3. [Ansible](https://docs.ansible.com/)
4. [Setup K8s Kubeadm](./setup-k8s/Readme.md)

- Setup Kubernetes com `Kubespray`

1. [Setup K8s Kubespray](./setup-k8s-kubespray/kubespray/README.md)
2. [Kubespray](https://github.com/kubernetes-sigs/kubespray)

- Setup Kubernetes com `Kind`

1. [Setup K8s Kind](./setup-kind/Readme.md)
2. [Kind](https://kind.sigs.k8s.io/)

## ♟️ Requisitos computacionais

- Utilizando o Setup Kubernetes com kubeadm.
- [Na documentação oficial do kubernetes é exigido de cada nó do cluster as seguintes configurações:](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/)

    - Um host linux compatível
    - 2GB de RAM
    - 2CPUs
    - Conectividade de rede entre os nós

```console
OBS: para termos uma experiência comportamental mais próxima da realidade, será preparado um cluster com 3 nós: o primeiro com a finalidade de ser o gerenciador, que na nomenclatura do kubernetes é chamado de control-plane e os demais como nós responsáveis por abrigar os workloads, chamados de worker nodes. Sendo assim, teremos que ter livre ao menos 6GB de RAM para subir essa infraestrutura. 
```

## 📑 Roteiro de preparação da CKA

- [x] Arquitetura do Cluster, instalação e configuração
- [x] Workloads e Scheduling
- [x] Services and Networkings
- [x] Storage
- [x] Troubleshooting


## 🧮 Laboratórios

- [ ] [Laboratórios: Praticar com exercicios e desafios](./desafios/Readme.md)

## 📄 Referências
- [ Documentação Kubernetes ](https://kubernetes.io/) 
- [ Curso preparatório: Certificação CKA | Kubernetes v1.26 ] 
