# Giraf Production Swarm  (GPS)
Repo for the production swarm that is serving the Giraf Project

To deploy the swarm into production ssh into the master00 server and make a git pull in the repo and run the following command:

```bash
docker stack deploy -c docker-stack.yml GirafStack
```

Verify that the stack was deployed correctly with:

```bash
docker stack services GirafStack
```

And verify that all services a up and running. 
