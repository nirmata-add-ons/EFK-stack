# EFK-stack (Elasticsearch, Fluentd, and Kibana (EFK) stack)

This README documents the EFK stack integration as Nirmata add-on on Kubernetes clusters.

### What is the EFK stack?

Together Elasticsearch, FluentD, and Kibana are commonly referred to as the EFK stack which is a centralized logging solution for Kubernetes.

Elasticsearch is a real-time, distributed, and scalable search engine which allows for full-text and structured search, as well as for analytics. It is commonly used to index and search through large volumes of log data, but can also be used to search many different kinds of documents.

"**Elasticsearch**" is commonly deployed alongside Kibana, a powerful data visualization frontend and dashboard for Elasticsearch. "**Kibana**" allows you to explore your Elasticsearch log data through a web interface, and build dashboards and queries to quickly answer questions and gain insight into your Kubernetes applications. "**Fluentd**" will collect, transform, and ship log data to the Elasticsearch backend. Fluentd is a popular open-source data collector that we’ll set up on our Kubernetes nodes to tail container log files, filter and transform the log data, and deliver it to the Elasticsearch cluster, where it will be indexed and stored.



### How do I get set up?
1. Clone this repository or add its contents to your own private Git repository.
2. Create a Nirmata catalog application with a Git upstream and select the EFK-stack repository. You can optionally select the kustomization.
3. Edit the catalog application and select an add-on category (e.g. Logging). This is required to select the application as an add-on.
4. Update a Cluster Type, or create a new one, and select the EFK-stack add-on application in the "Add-Ons" section. Ensure that the namespace you use is "**fluentd-es**" and environment is "fluentd-es-< cluster-name >"
5. Create clusters using the cluster type.
6. If the addon is to be added to a running cluster, create an environment with the name "**fluentd-es**" and choose this environment while deploying the application. 

### Note: The storage request is 1Gi by default and this application needs dynamic volume provisioning enabled to create a storage volume. Please refer to the "**open-ebs**" repository for more details on integrating openebs as a dynamic volume provisioning in Nirmata
