### How to Install the it-fse-gtw-config service

1. ### Create the ConfigMap

Before installing the **it-fse-gtw-config-cm** service, you need to create a ConfigMap that contains the required configuration for the service. <br>
This allows the service to use custom settings or environment variables needed during installation and runtime.

To create the configMap named **it-fse-gtw-config-cm** in the Kubernetes cluster required from the service:

```bash
kubectl create configmap it-fse-gtw-config-cm --from-file=application.properties=config\application.properties
```
*Output:*
>configmap/it-fse-gtw-config-cm created

or 
Verify the ConfigMap has been created successfully by running:

```bash
kubectl get configmap it-fse-gtw-config-cm
```

2. ### Install the Service

Once the ConfigMap has been created, you can install the it-fse-gtw-config itself.

To upgrade or install the service:

1. Download the Helm chart for the service either by using the helm fetch command or by directly retrieving the service from the repository.

2. Upgrade or Install the service:
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

3. To remove the service installed so far:
```bash
helm delete it-fse-gtw-config
```

---

### Rules Manager

To create the configMap named **it-fse-gtw-rules-manager-cm** in the Kubernetes cluster required from the service:

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

To create the configMap named **it-fse-gtw-dispatcher-cm** in the Kubernetes cluster required from the service:

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

To create the configMap named **it-fse-gtw-validator-cm** in the Kubernetes cluster required from the service:

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

To create the configMap named **it-fse-gtw-fhir-mapping-engine-cm** in the Kubernetes cluster required from the service:

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

To create the configMap named **it-fse-gtw-indexer-cm** in the Kubernetes cluster required from the service:

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

To create the configMap named **it-fse-gtw-ini-client-cm** in the Kubernetes cluster required from the service:

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

To create the configMap named **it-fse-gtw-garbage-cm** in the Kubernetes cluster required from the service:

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

To create the configMap named **it-fse-gtw-status-check-cm** in the Kubernetes cluster required from the service:

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

To create the configMap named **it-fse-gtw-status-manager-cm** in the Kubernetes cluster required from the service:

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
