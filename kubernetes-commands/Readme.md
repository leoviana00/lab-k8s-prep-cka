# Revisando - Kubernetes Commands

Lista de comandos de uso geral para gerenciamento do Kubernetes:

- [PODS](#pods)
- [Create Deployments](#create-deployments)
- [Scaling PODs](#scaling-pods)
- [POD Upgrade / History](#pod-upgrade-and-history)
- [Services](#services)
- [Volumes](#volumes)
- [Secrets](#secrets)
- [ConfigMaps](#configmaps)
- [Ingress](#ingress)
- [Horizontal Pod Autoscalers](#horizontal-pod-autoscalers)
- [Scheduler](#scheduler)
- [Taints and Tolerations](#tains_and_tolerations)
- [Troubleshooting](#troubleshooting)
- [Role Based Access Control (RBAC)](#role_based_access_control)
- [Security Contexts](#security_contexts)
- [Pod Security Policies](#pod_security_policies)
- [Network Policies](#network_policies)
- [YAML](#yaml)
- [Kubeadm](#KUBEADM)
- [ETCD](#ETCD)


## PODS

```
$ kubectl get pods
$ kubectl get pods --all-namespaces
$ kubectl get pod monkey -o wide
$ kubectl get pod monkey -o yaml
$ kubectl describe pod monkey
```

## Create Deployments

Criar um deployment

```bash
$ kubectl run monkey --image=ubuntu --command sleep 1d --record
```

```bash
$ kubectl create deploy monkey --image=ubuntu 
```

## Scaling PODs

```bash
$ kubectl scale deployment/POD_NAME --replicas=N
```

## POD Atualização e histórico

#### Listar histórico de deployments

```bash
$ kubectl rollout history deployment/DEPLOYMENT_NAME
```

#### Ir para a revisão específica

```bash
$ kubectl rollout undo deployment/DEPLOYMENT_NAME --to-revision=N
```

## Services

Listar serviços

```
$ kubectl get services
```

Expor PODs como serviços (creates endpoints)

```
$ kubectl expose deployment/monkey --port=2001 --type=NodePort
```

## Volumes

Litar `Persistent Volumes` e `Persistent Volumes Claims`:

```
$ kubectl get pv
$ kubectl get pvc
```

## Secrets

```
$ kubectl get secrets
$ kubectl create secret generic --help
$ kubectl create secret generic mysql --from-literal=admin=root --from-literal=password=123456
$ kubectl get secrets mysql -o yaml
```
## ConfigMaps

```
$ kubectl create configmap foobar --from-file=config.js
$ kubectl get configmap foobar -o yaml
```

## DNS

Listar DNS-PODs:

```
$ kubectl get pods --all-namespaces |grep dns
```

Verifique o DNS para pod nginx (assumindo que um POD/contêiner busybox esteja em execução)

```
$ kubectl exec -ti busybox -- nslookup nginx
```

> Nota: o kube-proxy em execução nos nós do trabalhador gerencia serviços e define regras de iptables para direcionar o tráfego.

## Ingress

Comandos para gerenciar o tipo de serviço Ingress for ClusterIP:

```
$ kubectl get ingress
$ kubectl expose deployment ghost --port=2368
```

Especificações de entrada:

- [backend](https://github.com/kubernetes/ingress/tree/master/examples/deployment/nginx)
 
## Horizontal Pod Autoscaler

Quando o heapster é executado:

```
$ kubectl get hpa
$ kubectl autoscale --help
```

## DaemonSets

```
$ kubectl get daemonsets
$ kubectl get ds
```

## Scheduler

Política baseada em NodeSelector:

```
$ kubectl label node node-01 foo=bar
```

Ligação de nó por meio do servidor API:

```
$ kubectl proxy 
$ curl -H "Content-Type: application/json" -X POST --data @binding.json http://localhost:8001/api/v1/namespaces/default/pods/foobar-sched/binding
```

## Tains and Tolerations

```
$ kubectl taint node master foo=bar:NoSchedule
```

## Troubleshooting

```
$ kubectl describe
$ kubectl logs
$ kubectl exec
$ kubectl get nodes --show-labels
$ kubectl get events
```

Docs Cluster: 
- https://kubernetes.io/docs/tasks/debug-application-cluster/debug-cluster/
- https://github.com/kubernetes/kubernetes/wiki/Debugging-FAQ

## Role Based Access Control

- Role
- ClusterRule
- Binding
- ClusterRoleBinding

```
$ kubectl create role fluent-reader --verb=get --verb=list --verb=watch --resource=pods
$ kubectl create rolebinding foo --role=fluent-reader --user=minikube
$ kubectl get rolebinding foo -o yaml
```

## Security Contexts

Docs: https://kubernetes.io/docs/tasks/configure-pod-container/security-context/

- spec
 - securityCOntext
   - runAsNonRoot: true
   
## Pod Security Policies

Docs: https://github.com/kubernetes/kubernetes/blob/master/examples/podsecuritypolicy/rbac/README.md

## Network Policies

Isolamento de rede no nível do pod usando anotações

```
$ kubectl annotate ns <namespace> "net.beta.kubernetes.io/network-policy={\"ingress\": {\"isolation\": \"DefaultDeny\"}}"
```

Mais sobre políticas de rede como recurso:

https://kubernetes.io/docs/tasks/administer-cluster/declare-network-policy/

## YAML

### Single Container
```YAML
apiVersion: v1
kind: Pod
metadata:
  name: busybox
spec:
  containers:
    - image: busybox
      name: busybox
      command:
        - sleep
        - "3600"
```

### Double container in a pod
```YAML
apiVersion: v1
kind: Pod
metadata:
  name: two-containers
spec:

  restartPolicy: Never

  volumes:
  - name: shared-data
    emptyDir: {}

  containers:

  - name: nginx-container
    image: nginx
    volumeMounts:
    - name: shared-data
      mountPath: /usr/share/nginx/html

  - name: debian-container
    image: debian
    volumeMounts:
    - name: shared-data
      mountPath: /pod-data
    command: ["/bin/sh"]
    args: ["-c", "echo Hello from the debian container > /pod-data/index.html"]
```

### Single init container
```YAML
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
  labels:
    app: myapp
spec:
  containers:
  - name: myapp-container
    image: busybox
    command: ['sh', '-c', 'echo A aplicação está rodando! && sleep 3600']
  initContainers:
  - name: init-myservice
    image: busybox:1.28
    command: ['sh', '-c', 'until nslookup myservice; do echo aguardando pelo serviço: myservice; sleep 2; done;']
  - name: init-mydb
    image: busybox:1.27
    command: ['sh', '-c', 'until nslookup mydb; do echo aguardando pelo serviço: mydb; sleep 2; done;']
```

### Persistent Volume
```YAML
kind: PersistentVolume
apiVersion: v1
metadata:
  name: pv0001
  labels:
    type: local
spec:
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/Users/nahi/kubernetes/pv"
```

### Namespace
```YAML
kind: Namespace
metadata:
  name: myns
```
### Jobs
```YAML
apiVersion: batch/v1
kind: Job
metadata:
  name: busybox
spec:
  template:
    metadata:
      name: busybox
    spec:
      containers:
      - name: busybox
        image: busybox
        command: ["echo",  "hello", "world"]
      restartPolicy: Never
  completions: 10
  parallelism: 2
```
  
### Busybox w/ secret
```YAML
apiVersion: v1
kind: Pod
metadata:
  name: busybox-with-secret
spec:
  containers:
    - image: busybox-with-secret
      name: busybox
      imagePullPolicy: IfNotPresent
      volumeMounts:
        - mountPath: /busy
          name: test
      env:
        - name: MY_SECRET
          valueFrom:
            secretKeyRef:
              name: mysecret
              key: password
      command:
        - sleep
        - "3600"
  volumes:
    - name: test
      secret:
        secretName: mysecret
```

### Pod w/ Namespace
```YAML
apiVersion: v1
kind: Pod
metadata:
  namespace: myns
  name: redis
spec:
  containers:
  - image: redis:3.2
    imagePullPolicy: IfNotPresent
    name: redis
  restartPolicy: Always
```
 
### DaemonSet
```YAML
apiVersion: extensions/v1beta1
kind: DaemonSet
metadata:
  name: busybox-daemon
spec:
  template:
    metadata:
      labels:
        name: busybox-daemon
    spec:
      hostNetwork: true
      hostPID: true
      containers:
        - name: busybox
          image: busybox
          command:
            - sleep
            - "3600"
          securityContext:
            privileged: true
```

### Tolerations
```YAML
apiVersion: v1
kind: Pod
metadata:
  name: alpine
spec:
  tolerations:
    - key: node-role.kubernetes.io/master
      effect: NoSchedule
  containers:
    - image: alpine
      name: alpine
      command:
        - sleep
        - "3600"
```
## ETCD
```
etcdctl
https://coreos.com/etcd/docs/latest/v2/admin_guide.html
```

## Kubeadm
```
$> kubeadm token list
$> cat /etc/kubernetes/pki/tokens.csv
```