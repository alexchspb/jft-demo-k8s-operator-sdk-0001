# Description

There is a k8s Operator created `just for tests and learning` purposes. Basically it's just deploy number of pods with given image. For example.

```yaml
apiVersion: apps.alexchspb.ru/v1
kind: JftDemoOperatorSDK
metadata:
  name: jftdemooperatorsdk-sample
  namespace: jftdemooperatorsdks
spec:
  image: "alexchspb/jft-app-py-0001:930d1750"
  size: 1
```

## Manifests description

|#|Manifest filename|Description|
|-|-|-|
|1|manifests/1-namespace.yaml|Creates Namespace (`jftdemooperatorsdks` in our case)|
|2|manifests/2-service_account.yaml|Creates `SA` in k8s|
|3|manifests/3-role.yaml|Creates `ROLE` in k8s|
|4|manifests/4-role_binding.yaml|Makes `ROLE_BINDING`|
|5|manifests/5-custom-resource-definition.yaml|Creates `CRD`|
|6|manifests/6-deployment.yaml|Creates `Deployment` with uses `IMAGE` with the Operator (`alexchspb/jft-demo-k8s-operator-sdk-0001:latest`)|
|7|manifests/7-custom-resource-object.yaml|Creates object with `jftdemooperatorsdks` Kind|

## Operator deployment

```bash
kubectl apply -f 1-namespace.yaml
kubectl apply -f 2-service_account.yaml 
kubectl apply -f 3-role.yaml 
kubectl apply -f 4-role_binding.yaml 
kubectl apply -f 5-custom-resource-definition.yaml 
kubectl apply -f 6-deployment.yaml 
kubectl apply -f 7-custom-resource-object.yaml
```
