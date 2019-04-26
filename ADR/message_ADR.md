# Message Passing
# Date: 4/15/2019

# Status: Accepted
# Decision makers: William Hundahl

#### Meassage Passing 

- With the ansible script it is fairly easy to set up TCP connection between containers to allow for the separation of software within the application, making for faster development and build times. Message passing is implemented in this application to allow for the requests made on the frontend during interaction with the webclient layer, to be sent to the server layer which are then processed and sent to the database. 

#### Message passing using TCP connection, linked docker containers and environment variables 

- The Message assing is coded in using a TCP web socket connection between the webclient container using pyzmq and the server container which also contains pyzmq and opens on the same port to receive requests. The environment variables are instantiated in the ansible playbook file when provisioning the containers for both the web client and server. This could just be achieved through the linking of the containers but one would still need to provide information on the port to be accessed. 