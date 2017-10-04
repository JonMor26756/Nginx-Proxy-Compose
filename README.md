# Nginx-Proxy-Compose

_Pull Requests Welcome_

**Intro**

This is a Docker compose file for easily setting up Nginx-Proxy and Nginx-Proxy-Companion.


**Uses**

[jwilder/nginx-proxy](https://github.com/jwilder/nginx-proxy)

[Jrcs/docker-letsencrypt-nginx-proxy-companion](https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion)


**Setup**

You will need to setup a domain to use with this application 
(GoDaddy, Dynadot). After setting up a domain you can point it to 
your server of choice (AWS, DigitalOcean).
*Setting up of a domain and a server for use is beyond the scope 
of this application*

**Usage**

To clone this repository

> git clone --recursive https://github.com/JonMor26756/Nginx-Proxy-Compose.git

The sample application directory shows what an example application may look like.
This example uses a simple apache2 server docker-compose.yml which uses the .env 
file within it's folder to dictate the HOST, EMAIL, and VIRTUAL HOST variables to 
be used by Ngixn-Proxy and Nginx-Proxy-Companion to route traffic as well as, gather
lets'encrypt certificates for easy SSL implementation. 
You will need to modify the following file with for your sample application with domain
specific information. This file will contain variables for ease of use.

- sample-application/.env

You would then:

> cd Nginx-Proxy-Compose

> docker-compose up -d

leaving the Nginx-Proxy-Compose up and running.
Then

> cd sample-application

> docker-compose up -d

> docker network connect (sample-application-network-name) nginx-proxy

to launch you application

_IMPORTANT_
You must run the docker network command to connect your applicaiton to the nginx-proxy container
network or you will not have connectivity between Nginx-Proxy and your application and consequently
no proxy as well as, no SSL.


To add applications which will use the proxy provided use the docker-compose.yml and
.env files provided within /sample-application.

To execute the project deployment run the following command:

> docker-compose up -d
