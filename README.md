# About

Source for Google Click to Deploy solutions listed on Google Cloud Marketplace.

# Disclaimer

This is not an officially supported Google product.

# :warning: Log4j Vulnerabilities

Some solutions hosted in this repository may be impacted by Log4j vulnerabilities
and are currently awaiting vendor updates.
Please refer to the list below for information which solutions are depending
on Log4j framework and corresponding status.

## Virtual Machines

| | Solution | Status |
| --- | --- | --- |
| &#x274C; | elasticsearch | Vulnerable, Log4j 2 |
| &#x274C; | kafka | Vulnerable, Log4j 1 |
| &#x274C; | logstash | Vulnerable, Log4j 2 |
| &#x274C; | magento | Vulnerable, Log4j 2 |
| &#x2705; | neo4j | Updated, no impact |
| &#x2705; | solr | Updated, no impact |
| &#x274C; | sonarqube | Vulnerable, Log4j 2 |
| &#x274C; | alfresco | Vulnerable, Log4j 1 |
| &#x274C; | liferay | Vulnerable, Log4j 1 |
| &#x274C; | pimcore | Vulnerable, Log4j 1 |
| &#x274C; | tensorflow | ??? |

## Kubernetes Applications

| | Solution | Status |
| --- | --- | --- |
| &#x274C; | activemq | Vulnerable, Log4j 1 |
| &#x274C; | elastic-gke-logging | Vulnerable, Log4j 2 |
| &#x274C; | elasticsearch | Vulnerable, Log4j 2 |
| &#x2705; | hazelcast | Updated, no impact |
| &#x274C; | kafka | Vulnerable, Log4j 1 |
| &#x274C; | magento |  Vulnerable due to elasticsearch dependency |
| &#x2705; | neo4j-ce | Mitigated |
| &#x2705; | solr | Mitigated |
| &#x274C; | sonarqube | Vulnerable due to elasticsearch dependency |
| &#x2705; | rabbitmq | Not affected |
| &#x274C; | zookeeper | Vulnerable due to elasticsearch dependency |

# Cloud Build CI

This repository uses Cloud Build for continuous integration. Each type of application has its own configuration file.

For detailed information on each configuration, see the following documentations:

*   [Docker images](docker/README.md#cloud-build-ci)
*   [K8s applications](k8s/README.md#cloud-build-ci)
*   [VM applications](vm/README.md#cloud-build-ci)

## GCB custom worker pools

The Cloud Build configurations use Google Cloud Build (GCB) custom worker pools.

If you want to create a new worker pool, run the following command:

```shell
gcloud beta builds worker-pools create gcb-workers-pool-e2 \
  --project=[PROJECT_ID] \
  --peered-network=projects/[NETWORK_PROJECT_NUMBER]/global/networks/default \
  --region=us-central1 \
  --worker-machine-type=e2-standard-2
```

Where:

*   `[PROJECT_ID]` is the GCP project ID where you want to create your custom worker pool.
*   `[NETWORK_PROJECT_NUMBER]` is the project number of the Cloud project that holds your VPC network.

For more information, see the
[gcloud beta builds worker-pools commands](https://cloud.google.com/sdk/gcloud/reference/beta/builds/worker-pools/).
