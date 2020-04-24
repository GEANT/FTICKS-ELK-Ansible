# FTICKS-ELK-Ansible

# Ansible Playbook to deploy Federation FTICKS collector based on ELK stack

1. [The Playbook](#the-playbook)
2. [Contacts](#contacts)

## The Playbook

This playbook provides an easy way to deploy a SAML2 federation FTICKS collector node. 

It will install and configure:

1. Elasticsearch cluster (role elastic.elasticsearch)
2. Logstash (role elastic.logstash)
3. Kibana + Nginx (role elastic.kibana)

A sample inventory is also available in the directory "inventory". It contans a group_vars directory.

## Deployment

To use this ansible playbook, one needs to define the inventory and fill in the information in the group_vars indicated with CHANGE ME.

To deploy the FTICKS collector, one needs to execute

ansible-playbook -i inventory multinode.yml

## Usage

The deployment will deploy a secure Elastic cluster. The Kibana is available on the designated node on port 443, where public readonly access is available.
On the Kibana node port 8443, there is a secure access to the Kibana.

## IDPs

The Federation IDPs need to send data on port 514 to the Logstash node IP address.

## NOTE

The Firewall is not configured using this ansible playbook. Only on logstash node a port redirection is done from port 514 to port 1514, since Logstash does not listen on privilege ports.
