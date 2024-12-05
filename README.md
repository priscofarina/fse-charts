# Fascicolo Sanitario 2.0

# Services to be Installed

Below the list of each microservice that needs to be installed:

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
kubectl create secret docker-registry name-secret-registry --docker-server=registry-to-use --docker-username=userPull --docker-password=userPassword
```

**What it does:**<br>
This command creates a Kubernetes secret named name-secret-registry that contains Docker registry credentials.<br>
The secret will store the **docker-server**, **docker-username**, and **docker-password**, which are necessary for Kubernetes to authenticate and pull Docker images from a specified registry.<br>

**Breakdown of the command:**<br>
**kubectl**: The command-line tool used to interact with a Kubernetes cluster.<br>
**create secret docker-registry**: This creates a Docker registry secret that stores credentials for accessing a Docker registry.<br>

**name-secret-registry**: This is the name of the secret being created. In this case, the secret is named name-secret-registry.<br>
**--docker-server**=registry-to-use: Specifies the URL of the Docker registry to authenticate against (e.g., Docker Hub, a private registry, etc.). Replace registry-to-use with the actual URL of the registry (e.g., https://index.docker.io/v1/ or a private registry URL).<br>
**--docker-username**=userPull: The username used to authenticate with the Docker registry. Replace userPull with the actual username for accessing the registry.<br><br>
**--docker-password**=userPassword: The password associated with the specified Docker username (userPull). Replace userPassword with the actual password or access token.

**Example of usage:**<br>
**TO NOTICE:** <br>
**The azregdevops secret will be used in the installation phase, but you can replace this value with the value you have chosen in the step of secret creation**

```bash
kubectl create secret docker-registry azregdevops --docker-server=registry-to-use --docker-username=userPull --docker-password=userPassword
```

## Helm Repository Management

The following commands can be used to search for and retrieve a specific version of one of the services mentioned above:

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
helm fetch repo fse/it-fse-gtw-rules-manager --versions
```

```bash
helm repo update fse
```


**To download a specific version:**
```bash
helm fetch <nome-repo>/<nome-chart> --version <versione-chart> 
```

Example:
**To download the 0.1.0 version listed from the search command for the it-fse-gtw-rules-manager service:**
```bash
helm fetch fse/it-fse-gtw-rules-manager --version 0.1.0
```
This downloads the package which can be used in the installation phase later.

---
## Service Installation Guide 

- [*it-fse-gtw-config*](it-fse-gtw-config/installation-guide.md)
- [*it-fse-gtw-rules-manager*](https://github.com/ministero-salute/it-fse-gtw-rules-manager)
- [*it-fse-gtw-dispatcher*](https://github.com/ministero-salute/it-fse-gtw-dispatcher)
- [*it-fse-gtw-validator*](https://github.com/ministero-salute/it-fse-gtw-validator)
- [*it-fse-gtw-fhir-mapping-engine*](https://github.com/ministero-salute/it-fse-gtw-fhir-mapping-engine)
- [*it-fse-gtw-indexer*](https://github.com/ministero-salute/it-fse-gtw-indexer)
- [*it-fse-gtw-ini-client*](https://github.com/ministero-salute/it-fse-gtw-ini-client)
- [*it-fse-gtw-garbage*](https://github.com/ministero-salute/it-fse-gtw-garbage)
- [*it-fse-gtw-status-check*](https://github.com/ministero-salute/it-fse-gtw-status-check)
- [*it-fse-gtw-status-manager*](https://github.com/ministero-salute/it-fse-gtw-status-manager)
- 
---

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
