## Certificate details

- Identifique o arquivo de certificado usado para o servidor kube-api

```bash
cat /etc/kubernetes/pki/apiserver.crt
```

- Identifique o arquivo de certificado usado para autenticar o kube-apiserver como cliente do servidor ETCD.

```bash
cat /etc/kubernetes/pki/apiserver-etcd-client.crt
```

- Identifique a chave usada para autenticar o servidor kubeapi no servidor kubelet.

```bash
cat /etc/kubernetes/pki/apiserver-kubelet-client.key
```

- Identifique o certificado do servidor ETCD usado para hospedar o servidor ETCD

```bash
cat /etc/kubernetes/pki/etcd/server.crt
```

- Identifique o certificado raiz CA do servidor ETCD usado para servir o servidor ETCD.
- O ETCD pode ter sua própria CA. Portanto, este pode ser um certificado CA diferente daquele usado pelo servidor kube-api.

```bash
cat /etc/kubernetes/pki/etcd/ca.crt
```

- Qual é o nome comum (CN) configurado no certificado de servidor da API Kube?
- Sintaxe OpenSSL: `OpenSSL X509 -in FILH -PATH.CRT -TEXT -NOOUT`

```bash
openssl x509 -in /etc/kubernetes/pki/apiserver.crt -text -noout 
```

- Qual é o nome da CA que emitiu o certificado do servidor API Kube?

```bash
openssl x509 -in /etc/kubernetes/pki/apiserver.crt -text -noout | grep -i issuer
```

- Qual dos nomes alternativos abaixo não está configurado no certificado do servidor API Kube?

```bash
openssl x509 -in /etc/kubernetes/pki/apiserver.crt -text -noout | grep -i alternative -A1
```

- Qual é o Nome Comum (CN) configurado no certificado do Servidor ETCD?

```bash
openssl x509 -in /etc/kubernetes/pki/etcd/server.crt -text -noout
```

- How long, from the issued date, is the Kube-API Server Certificate valid for?
- File: /etc/kubernetes/pki/apiserver.crt

```bash
openssl x509 -in /etc/kubernetes/pki/apiserver.crt -text -noout | grep -i validity -A2
```

- How long, from the issued date, is the Root CA Certificate valid for?
- File: /etc/kubernetes/pki/ca.crt

```bash
openssl x509 -in /etc/kubernetes/pki/etcd/ca.crt -text -noout | grep -i validity -A2
```