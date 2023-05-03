# ELK Stack Deployment on Kubernetes

This is a guide to deploy the ELK stack (Elasticsearch, Logstash, and Kibana) on Kubernetes using Helm charts.
Prerequisites

Before deploying the ELK stack, make sure you have the following prerequisites:

    A Kubernetes cluster
    Connection to your Kubernetes cluster
    At least two nodes in your node pool (you can check using the command kubectl get node)

Deployment

Clone the repository using the following command:
    
    git clone https://github.com/sonulodha/elk.git

Change the directory to the cloned repository:

    cd elk

Deploy Filebeat using the following command:

    cd filebeat

    helm install filebeat .

Deploy Logstash using the following command:
    
    cd ../logstash

    helm install logstash .

Check the status of the Logstash pod:

    kubectl get pod


Deploy Elasticsearch using the following command:

    cd ../elasticsearch
    
    helm install elasticsearch .

Check the status of the Elasticsearch pod:

    kubectl get pod

Deploy Kibana using the following command:

    cd ../kibana

    helm install kibana .

    kubectl get svc (check kibanan svc ip )
    
 Open kibana dashboard 
 
    http://<ip>:5601

  Use Kibana username and password to login kibana dashoard
    username: elastic
    password: kubectl get secrets --namespace=default elasticsearch-master-credentials -ojsonpath='{.data.password}' | base64 -d

Check the status of the Kibana pod:
    
    kubectl get pod

Verify that all the components of the ELK stack are running using the following command:

    helm list
