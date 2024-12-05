# Fascicolo Sanitario 2.0

# Services to be Installed

Below is the list of each microservice that needs to be installed:

- [*it-fse-gtw-config*](https://github.com/ministero-salute/it-fse-gtw-config)
- [*it-fse-gtw-rules-manager*](https://github.com/ministero-salute/it-fse-gtw-rules-manager)
- [*it-fse-gtw-dispatcher*](https://github.com/ministero-salute/it-fse-gtw-dispatcher)
- [*it-fse-gtw-validator*](https://github.com/ministero-salute/it-fse-gtw-validator)
- [*it-fse-gtw-fhir-mapping-engine*](https://github.com/ministero-salute/it-fse-gtw-fhir-mapping-engine)
- [*it-fse-gtw-indexer*](https://github.com/ministero-salute/it-fse-gtw-indexer)
- [*it-fse-gtw-ini-client*](https://github.com/ministero-salute/it-fse-gtw-ini-client)
- [*it-fse-gtw-garbage*](https://github.com/ministero-salute/it-fse-gtw-garbage)
- [*it-fse-gtw-status-check*](https://github.com/ministero-salute/it-fse-gtw-status-check)
- [*it-fse-gtw-status-manager*](https://github.com/ministero-salute/it-fse-gtw-status-manager)

# Steps to Install GTW

## Define the Secret on the Cluster

```bash
kubectl create secret docker-registry azregdevops --docker-server=registry-to-use --docker-username=userPull --docker-password=userPassword
```

## Helm Repository Management

You can use the following commands to search for and fetch a specific version of one of the services listed above:

```bash
helm repo add fse https://ministero-salute.github.io/it-fse-gtw-helm
helm repo update fse
helm search repo fse/it-fse-gtw-rules-manager --versions
```

| Name                        | Chart Version | App Version | Description                              |
|-----------------------------|---------------|-------------|------------------------------------------|
| fse/it-fse-gtw-rules-manager | 0.1.0         | xxx       | Service of Fascicolo Sanitario Electronico |
| ...                         | ...           | ...         | ...                                      |

The ```helm search``` can be used to fetch the latest version of each service.
It is important to update the repository before performing the search with the following command:

```bash
helm repo update fse
```

---

### Config

To create the configMap named **it-fse-gtw-config-cm** in the Kubernetes cluster required from the service:

```bash
kubectl create configmap it-fse-gtw-config-cm --from-file=application.properties=config\application.properties
```
*Output:*
>configmap/it-fse-gtw-config-cm created

To upgrade or install the service:
```bash
helm upgrade --install it-fse-gtw-config it-fse-gtw-config-0.1.0.tgz --set "imagePullSecrets[0].name=azregdevops"
```
*Output:*
>Release "it-fse-gtw-rules-manager" does not exist. Installing it now.
>NAME it-fse-gtw-config
>LAST DEPLOYED: Fri Nov 29 11:05:42 2024  
>NAMESPACE: default  
>STATUS: deployed  
>REVISION: 1  
>TEST SUITE: None

*To delete:*

```bash
helm delete it-fse-gtw-config
```

---

### Rules Manager

To create the configMap named it-fse-gtw-rules-manager-cm in the Kubernetes cluster required from the service:

```bash
kubectl create configmap it-fse-gtw-rules-manager-cm --from-file=application.properties=path/al/file/application.properties --from-file=truststore.jks=path/al/file/truststore.jks
```
*Output:*
>configmap/it-fse-gtw-rules-manager-cm created

To upgrade or install the service:
```bash
helm upgrade --install it-fse-gtw-rules-manager it-fse-gtw-rules-manager-0.1.0.tgz --set "imagePullSecrets[0].name=azregdevops"
```
*Output:*
>Release "it-fse-gtw-rules-manager" does not exist. Installing it now.
>NAME it-fse-gtw-rules-manager  
>LAST DEPLOYED: Fri Nov 29 11:05:42 2024  
>NAMESPACE: default  
>STATUS: deployed  
>REVISION: 1  
>TEST SUITE: None  

*To delete:*

```bash
helm delete it-fse-gtw-rules-manager
```

### Dispatcher

To create the configMap named it-fse-gtw-dispatcher-cm in the Kubernetes cluster required from the service:

```bash
kubectl create configmap it-fse-gtw-dispatcher-cm --from-file=application.properties=config\application.properties --from-file=truststore.jks=config\truststore.jks
```
*Output:*
>configmap/it-fse-gtw-dispatcher created

To upgrade or install the service:

```bash
helm upgrade --install it-fse-gtw-dispatcher it-fse-gtw-dispatcher-0.1.0.tgz --set "imagePullSecrets[0].name=azregdevops"
```
*Output:*
>Release "it-fse-gtw-dispatcher" does not exist. Installing it now.
>NAME it-fse-gtw-dispatcher
>LAST DEPLOYED: Fri Nov 29 11:05:42 2024  
>NAMESPACE: default  
>STATUS: deployed  
>REVISION: 1  
>TEST SUITE: None

*To delete:*

```bash
helm delete it-fse-gtw-dispatcher
```

### Validator

To create the configMap named it-fse-gtw-validator-cm in the Kubernetes cluster required from the service:

```bash
kubectl create configmap it-fse-gtw-validator-cm --from-file=application.properties=config\application.properties --from-file=truststore.jks=config\truststore.jks
```
*Output:*
>configmap/it-fse-gtw-validator-cm created

To upgrade or install the service:

```bash
helm upgrade --install it-fse-gtw-validator it-fse-gtw-validator-0.1.0.tgz --set "imagePullSecrets[0].name=azregdevops"
```
*Output:*
>Release "it-fse-gtw-validator" does not exist. Installing it now.
>NAME it-fse-gtw-validator
>LAST DEPLOYED: Fri Nov 29 11:05:42 2024  
>NAMESPACE: default  
>STATUS: deployed  
>REVISION: 1  
>TEST SUITE: None

*To delete:*

```bash
helm delete it-fse-gtw-validator
```


### FHIR

To create the configMap named it-fse-gtw-fhir-mapping-engine-cm in the Kubernetes cluster required from the service:

```bash
kubectl create configmap it-fse-gtw-fhir-mapping-engine-cm --from-file=application.properties=config\application.properties
```
*Output:*
>configmap/it-fse-gtw-fhir-mapping-engine-cm created

To upgrade or install the service:

```bash
helm upgrade --install it-fse-gtw-fhir-mapping-engine it-fse-gtw-fhir-mapping-engine-0.1.0.tgz --set "imagePullSecrets[0].name=azregdevops"
```
*Output:*
>Release "it-fse-gtw-fhir-mapping-engine" does not exist. Installing it now.
>NAME it-fse-gtw-fhir-mapping-engine
>LAST DEPLOYED: Fri Nov 29 11:05:42 2024  
>NAMESPACE: default  
>STATUS: deployed  
>REVISION: 1  
>TEST SUITE: None

*To delete:*

```bash
helm delete it-fse-gtw-fhir-mapping-engine
```


### Indexer

To create the configMap named it-fse-gtw-indexer-cm in the Kubernetes cluster required from the service:

```bash
kubectl create configmap it-fse-gtw-indexer-cm --from-file=application.properties=config\application.properties --from-file=truststore.jks=config\truststore.jks
```
*Output:*
>configmap/it-fse-gtw-indexer-cm created

To upgrade or install the service:

```bash
helm upgrade --install it-fse-gtw-indexer it-fse-gtw-indexer-0.1.0.tgz --set "imagePullSecrets[0].name=azregdevops"
```
*Output:*
>Release "it-fse-gtw-indexer" does not exist. Installing it now.
>NAME it-fse-gtw-indexer
>LAST DEPLOYED: Fri Nov 29 11:05:42 2024  
>NAMESPACE: default  
>STATUS: deployed  
>REVISION: 1  
>TEST SUITE: None

*To delete:*

```bash
helm delete it-fse-gtw-indexer
```

### Ini-client

To create the configMap named it-fse-gtw-ini-client-cm in the Kubernetes cluster required from the service:

```bash
kubectl create configmap it-fse-gtw-ini-client-cm --from-file=application.properties=config\application.properties --from-file=truststore.jks=config\truststore.jks --from-file=S1GTW-INI.jks=config\S1GTW-INI.jks --from-file=A1GTW-INI.jks=config\A1GTW-INI.jks
```
*Output:*
>configmap/it-fse-gtw-ini-client-cm created

To upgrade or install the service:

```bash
helm upgrade --install it-fse-gtw-ini-client it-fse-gtw-ini-client-0.1.0.tgz --set "imagePullSecrets[0].name=azregdevops"
```
*Output:*
>Release "it-fse-gtw-ini-client" does not exist. Installing it now.
>NAME it-fse-gtw-ini-client
>LAST DEPLOYED: Fri Nov 29 11:05:42 2024  
>NAMESPACE: default  
>STATUS: deployed  
>REVISION: 1  
>TEST SUITE: None

*To delete:*

```bash
helm delete it-fse-gtw-ini-client
```


### Garbage

To create the configMap named it-fse-gtw-garbage-cm in the Kubernetes cluster required from the service:

```bash
kubectl create configmap it-fse-gtw-garbage-cm --from-file=application.properties=config\application.properties
```
*Output:*
>configmap/it-fse-gtw-garbage-cm created

To upgrade or install the service:

```bash
helm upgrade --install it-fse-gtw-garbage it-fse-gtw-garbage-0.1.0.tgz --set "imagePullSecrets[0].name=azregdevops"
```
*Output:*
>Release "it-fse-gtw-garbage" does not exist. Installing it now.
>NAME: it-fse-gtw-garbage
>LAST DEPLOYED: Fri Nov 29 12:38:41 2024
>NAMESPACE: default
>STATUS: deployed
>REVISION: 1
>TEST SUITE: None

*To delete:*

```bash
helm delete it-fse-gtw-garbage
```

### Status-check

To create the configMap named it-fse-gtw-status-check-cm in the Kubernetes cluster required from the service:

```bash
kubectl create configmap it-fse-gtw-status-check-cm --from-file=application.properties=config\application.properties
```
*Output:*
>configmap/it-fse-gtw-status-check-cm created

To upgrade or install the service:

```bash
helm upgrade --install it-fse-gtw-status-check it-fse-gtw-status-check-0.1.0.tgz --set "imagePullSecrets[0].name=azregdevops"
```
*Output:*
>Release  "it-fse-gtw-status-check" does not exist. Installing it now.
>NAME it-fse-gtw-dispatcher
>LAST DEPLOYED: Fri Nov 29 11:05:42 2024  
>NAMESPACE: default  
>STATUS: deployed  
>REVISION: 1  
>TEST SUITE: None

*To delete:*

```bash
helm delete it-fse-gtw-status-check
```


### Status-manager

To create the configMap named it-fse-gtw-status-manager-cm in the Kubernetes cluster required from the service:

```bash
kubectl create configmap it-fse-gtw-status-manager-cm --from-file=application.properties=config\application.properties --from-file=truststore.jks=config\truststore.jks
```
*Output:*
>configmap/it-fse-gtw-status-manager-cm created

To upgrade or install the service:

```bash
helm upgrade --install it-fse-gtw-status-manager it-fse-gtw-status-manager-1.2.0.tgz --set "imagePullSecrets[0].name=azregdevops"
```
*Output:*
>Release  "it-fse-gtw-status-manager" does not exist. Installing it now.
>NAME it-fse-gtw-status-manager
>LAST DEPLOYED: Fri Nov 29 11:05:42 2024  
>NAMESPACE: default  
>STATUS: deployed  
>REVISION: 1  
>TEST SUITE: None


*To delete:*

```bash
helm delete it-fse-gtw-status-manager
```

## Verify Resources

### Pods

```bash
kubectl get pods
```

Example output:

| NAME                                      | READY | STATUS  | RESTARTS | AGE |
|-------------------------------------------|-------|---------|----------|-----|
| it-fse-gtw-status-manager-845ccdf5dc-7jw7t | 0/1   | Running | 1        | 24s |

### ConfigMaps

```bash
kubectl get cm
```

Example output:

| NAME                              | DATA | AGE |
|-----------------------------------|------|-----|
|it-fse-gtw-config-cm               | 1    | 10m |
|it-fse-gtw-dispatcher-cm           | 2    | 10m |
|it-fse-gtw-fhir-mapping-engine-cm  | 1    | 10m |
|it-fse-gtw-garbage-cm              | 1    | 10m |
|it-fse-gtw-indexer-cm              | 2    | 10m |
|it-fse-gtw-ini-client-cm           | 4    | 10m |
|it-fse-gtw-rules-manager-cm        | 2    | 10m |
|it-fse-gtw-status-check-cm         | 1    | 10m |
|it-fse-gtw-status-manager-cm       | 2    | 10m |
|it-fse-gtw-validator-cm            | 2    | 10m |


### Kubernetes Secrets

```bash
kubectl get secrets
```

```bash
kubectl get secrets
```

Example output:


| NAME                     | TYPE                                | DATA | AGE  |
|--------------------------|-------------------------------------|------|------|
| azregdevops               | kubernetes.io/dockerconfigjson     | 1    | 14d  |
| kafka-secret              | Opaque                              | 16   | 111m |
| mongo-secret              | Opaque                              | 18   | 111m |
| pswcertclient-secret      | Opaque                              | 2    | 111m |
| ********************      | ********************                | ***  | *** |
```
