## Helm

- Instalação

```bash
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh

```
## Lab

- helm repo add ealenn https://ealenn.github.io/charts
- helm repo update
- helm upgrade -i tester ealenn/echo-server  --debug
- kubectl get svc
- helm list
- helm uninstall tester

```bash
helm repo add bitnami https://charts.bitnami.com/bitnamistudent@cp: ̃
helm fetch bitnami/apache --untarstudent@cp: ̃
cd apache/
```