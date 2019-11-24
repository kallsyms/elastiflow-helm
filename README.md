# ElastiFlow on Kubernetes With Helm

These are sample Helm `values.yaml` files to deploy a small (testing) size [ElastiFlow](https://github.com/robcowart/elastiflow) deployment on to kubernetes.

Charts used are elastic's own (not the ones in helm/stable). The logstash chart is not yet in elastic's helm repos (see [this issue](https://github.com/elastic/helm-charts/issues/370)), so the chart repo is submoduled in for convenience.

A few things are currently set for simplicity, but worth noting as it may be undesired behavior:
* elasticsearch is not persistent
* elasticsearch is setup to be a single node cluster
* ingest services are exposed with NodePorts

## Setup

```
git submodule update --init

helm repo add elastic https://helm.elastic.co
helm install --name elastiflow-elasticsearch elastic/elasticsearch -f ./elasticsearch.yaml
helm install --name elastiflow-kibana elastic/kibana -f ./kibana.yaml

helm install --name elastiflow-logstash ./helm-charts/logstash -f ./logstash.yaml
```
