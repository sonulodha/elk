# ELK Stack Deployment on Kubernetes

This is a guide to deploy the ELK stack (Elasticsearch, Logstash, and Kibana) on Kubernetes using Helm charts.
Prerequisites

Before deploying the ELK stack, make sure you have the following prerequisites:

    A Kubernetes cluster
    Connection to your Kubernetes cluster
    At least two nodes in your node pool (you can check using the command kubectl get node)

Deployment

    Clone the repository using the following command:

bash

git clone https://github.com/sonulodha/elk.git

    Change the directory to the cloned repository:

bash

cd elk

    Update the Elasticsearch Helm chart values.yml file to set antiAffinity from hard to soft:

bash

cd elasticsearch
vim values.yml

Update the following parameter in the file:

makefile

antiAffinity: soft

    Deploy Logstash using the following command:

bash

cd logstash
helm install logstash .

    Check the status of the Logstash pod:

arduino

kubectl get pod

    Deploy Filebeat using the following command:

bash

cd ../filebeat
helm install filebeat .

    Deploy Elasticsearch using the following command:

bash

cd ../elasticsearch
helm install elasticsearch .

    Check the status of the Elasticsearch pod:

arduino

kubectl get pod

    Deploy Kibana using the following command:

bash

cd ../kibana
helm install kibana .

    Check the status of the Kibana pod:

arduino

kubectl get pod

    Verify that all the components of the ELK stack are running using the following command:

helm list

Conclusion

In this guide, we have deployed the ELK stack on Kubernetes using Helm charts. You can now use this stack to collect, store, and visualize your application logs.
