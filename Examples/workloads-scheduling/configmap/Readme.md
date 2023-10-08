## Configmap

- Criando configmap

```bash
kubectl create configmap nameconfigmap-cm --from-literal=color1=black --from-literal=color2=red 
```

```bash
apiVersion: v1
kind: ConfigMap
metadata:
  name: nameconfigmap-cm
  namespace: default
data:
  color1: black
  color2: red
```