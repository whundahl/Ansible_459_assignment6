# Containers and Their Contents
# Date: 4/15/2019

# Status: Accepted
# Decision makers: William Hundahl

#### Containers

- There are three containers which are linked together during the start up of the ansible playbook. The first container to be started is the mongo container which holds a database image of mongo taken from the docker-hub. This container ingests two volumes of data, the configuration data and the operational data container within the application. 

- The next container to be started in the playbook is the server container which occurs after the execution of the database container to allow for a link between the two containers in the network to be established. After the web-client container is started which contains the operational layer that passes messages to the business logic layer in the server container, meaning these containers also need to be linked while making the correct environment variables available. 

#### Container Contents

Within the database container the image of mongo allows for the storage of the applications data, and as a result is the base layer of the application. Without this layer there would be little to no functionality in the application besides the presentation of html templates. The container is populated with some data but the startup for this container is lightweight and keeps the startup time for the database software short. But not short enough because we need to wait for the database to startup before continuing the script. 

Inside the webclient container there is an image of flask the python web framework, that is relatively simple and lightweight. All interface with the user is handled in this layer of the application within the web-container. There is also dependencies for pyzmq which allows this layer to interface with the web server layer containing the business logic of the application. 

The Web server container contains a couple dependencies for mongo and pyzmq as well, and all business logic and server code is carried out within this layer of the application. Additionally the code controls the message passing throughout the application from the webclient to the server and then to alter the database. The code waits for a message or http request and responds to it. 



