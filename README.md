# Giraf Production Swarm (GPS)
Repository for the Docker Swarm that serves the Giraf project. This repository contains the docker-compose.yml file, which dictates the structure of the swarm. The docker-compose.yml file needs to be cloned into the server to deploy the stack. After deploying the stack the compose file should be deleted as it contains the root password for the database.

## To run the swarm in production:
To deploy the swarm into production ssh into the master00 server and make a git pull in the repository and run the following command: `docker stack deploy -c docker-compose.yml GirafStack`

Verify that the stack was deployed correctly with: `docker stack services GirafStack`

## To run the swarm locally:
1. Download the docker-compose.yml or clone this repository. You can place the file wherever you want.
2. Download the swarm-nfs.zip (currently on Google Drive in the backend folder). Unzip the folder and place it in root directory (`cd /` in terminal). **(This is _not_ possible on Macs with Catalina)**

### In your terminal:
If any of these give a “permission denied”, simply put “sudo” in front of the command and enter your password if necessary.
1. Navigate(cd) into the folder where you placed the docker-compose.yml
2. Start docker.service: `service start docker` or `systemctl start docker`
3. Run `docker swarm init`
4. Run `docker stack deploy -c docker-compose.yml GirafStack`
5. Run `docker stack services GirafStack` to verify that all services are up and running

The docker-compose.yml file tells which images is being run for the different services (containers?). All the images for the Giraf project can be found on the [Docker Hub](https://hub.docker.com/r/giraf/web-api/tags).

For example, the “API_PROD” image is chosen to run in the [the compose file](docker-compose.yml), like this:
  `API_PROD:
      image: giraf/web-api:master-1-aspnet`

This uses the image “master-1-aspnet” found on [Docker Hub](https://hub.docker.com/r/giraf/web-api/tags).
