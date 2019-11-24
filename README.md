# ElastiFlow on Kubernetes With Helm

These are sample Helm `values.yaml` files to deploy a small (testing) size [ElastiFlow](https://github.com/robcowart/elastiflow) deployment on to kubernetes.

Charts used are elastic's own (not the ones in helm/stable). The logstash chart is not yet in elastic's helm repos (see [this issue](https://github.com/elastic/helm-charts/issues/370)), so the chart repo is submoduled in for convenience.

Ingest services are exposed with node ports for simplicity, but this can be easily changed to use a load balancer or ingress.

## Setup

```
git submodule update --init

helm repo add elastic https://helm.elastic.co
helm install --name elastiflow-elasticsearch elastic/elasticsearch -f ./elasticsearch.yaml
helm install --name elastiflow-kibana elastic/kibana -f ./kibana.yaml

helm install --name elastiflow-logstash ./helm-charts/logstash -f ./logstash.yaml
```
