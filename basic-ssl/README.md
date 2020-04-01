# A basic SSL Setup
This simple example is a demonstration of using Traefik to quickly deploy a very basic web service to a domain, and get an SSL certificate from Lets Encrypt into the bargain.

The docker-compose file is blatently copied from [the Traefik Docs](https://docs.traefik.io/user-guides/docker-compose/acme-tls/) example setup. See their guide for more information about specific sections of the compose file.

The one change made here is the use of a .env file to supply the domain name and email to the docker-compose.yml file. This makes the docker-compose script itself more portable.

## Setup this example

### Pre-requisites:
1. A server or system that:
 - has Docker and Docker-compose installed;
 - has a publicly accessible IP address;
 - has ports 80, 443 and 8080 available;
2. A domain or subdomain with an `A` type DNS record pointing to the server's IP Address.


### Process:
Code snippets given are for Ubuntu. Use the equivalents for your own system.


1. Find a suitable place on your server to deploy the service.
    - It's recommended to create a specific directory for running the docker container, for example: **/srv/web/basic-ssl/**
    - e.g. `mkdir /srv/web/basic-ssl -p`
2. Copy the contents of this folder onto the server, including:
    - docker-compose.yml
    - .env.example
3. Copy the .env.example to a new .env file and update the values. Eg:
    - `cp .env.example .env`
    - `nano .env`
    - enter your values for the domain or subdomain and email address.
4. Run `docker-compose up -d`
5. After a few moments, the who-am-i service should be accessible. Go to https://${your_domain}. You should see a simple text output showing some key details of your server.

You can also check the docker-compose logs by running `docker-compose logs`.

