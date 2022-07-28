# Kibana-on-kubernetes
 Deploy-kibana-on-kubernetes-using-manifest-files

Kibana is an free and open frontend application that sits on top of the Elastic Stack, providing search and data visualization capabilities for data indexed in Elasticsearch. Commonly known as the charting tool for the Elastic Stack (previously referred to as the ELK Stack after Elasticsearch, Logstash, and Kibana), Kibana also acts as the user interface for monitoring, managing, and securing an Elastic Stack cluster — as well as the centralized hub for built-in solutions developed on the Elastic Stack.

## Prerequisites
Make sure you have ElastikSearch deployed and it is up and running to connect to Kibana.

## kibana.yml
To deploy the kibana, we have here a deployment yaml file which uses a image kibana:5.6.4, which runs default on port 5601. And as we know kibana as a  data visualization tool that sits on top of the Elastic Stack, so it needs to connect to ElasticSearch. For that we will make the connection through service discovery, passing the url in the form of environment variable. Service discovery works in the form of <service name connecting to elastic.namespace containing the deployment/service.svc.cluster.local>. 

To apply the deployment use the following command:
```
kubectl apply -f kibana-deployment.yml
```

## service.yml
Then we have a simple ClusterIP service which connecting to our kibana deployment with targetPort set to default 5601.

To apply the deployment use the following command:
```
kubectl apply -f service.yml
```

## ingress.yml
At last an ingress file with ingressClass as "nginx" and a host name on which we will access our the kibana dashboard for all the search and data visualization tasks.

To apply the deployment use the following command:
```
kubectl apply -f ingress.yml
```
