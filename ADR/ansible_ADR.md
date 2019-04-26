# Ansible-Playbooks and using the Docker Module 
# Date: 4/15/2019

# Status: Accepted
# Decision makers: William Hundahl

#### Ansible with Docker Files and Requirements 

First off, Ansible is a playbook that defines the architecture of the project and how it should be built up, and or, provisioned. In the case of a server it needs to be provisioned with the correct software architecture in order to run correctly. 

In the case of this docker application the ansible script assumes that docker is already installed and that ansible is on the system where the application is to be spun up. In turn, the ansible script builds the images first for the three containers, creates volumes for the database, which store the persistent data for the application. The database container is then spun up, incorporating the two volumes and is built off the database image that was build in the prior tasks. After that the server and web container spin up using the images that were built in prior tasks as well. 

The Web container is linked to the server and the server to the web container. The database is then linked to the server container, and the application is then made available on port 8080 using the implicit localhost. 

#### Ansible Playbook Provisioning

Using ansible to provision applications provides several important features, which allow developers to provision machines with nothing but docker and ansible python dependency to spin up an instance of their web application. Additionally, the ansible script is written in yaml file format which is easy to read and is task oriented, presenting the developer with the ability to order the provisioned materials.  