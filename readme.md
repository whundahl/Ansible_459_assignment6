# Python, ZeroMQ, Mongo Example with Ansible Provisioning 

This example provides basic CRUD operations using a python flask container communicating using ZeroMQ to a business logic server layer further connected to a MongoDB container which acts and functions as the database layer. 

There are three ADRs listed within the ADR directory which list the decisions made in this application, while providing an explanation of the application at a high level. 

#### Please refer to the below section for starting and stopping of the application

Of interest:

- Use `ansible-playbook prvisionAppPlaybook.yaml` to build and run the application
- Use of a persistent storage volume
- Use of ZeroMQ to pass messages to the business logic layer
- Use Ansible to provision the containers with built images and docker volumes to persist the database information everytime the APP is started. 

To Stop the Application: 

- Use `ansible-playbook stopAppPlaybook.yaml` to stop the application 

To Stop the Application and Clean Up all Containers, Images, and Volumes: 

- Use `ansible-playbook removeAppPlaybook.yaml` to clean up and kill volumes and built images 