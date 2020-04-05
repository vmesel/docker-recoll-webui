# docker-recoll-webui

This repository is a Docker image to allow Recoll users to configure it's environment on any machine they want.

## What this Dockerfile does?

 - creates a python standalone recoll server inside a docker container listening on port 8000
 - indexes your sinology with the command `docker exec CONTAINER_ID recollindex`

# Installation Steps

Recoll is not a simple application to be installed in a standalone version, it's better developed with this docker image.

- in docker start the wizard to create a docker container from this image: mount `/homes` to `/homes` and mount `/homes/YOUR_USER_NAME` to `/root`, set up port mapping (defaults do also work)
- complete the following steps before you run the container
- download recoll.conf (https://raw.githubusercontent.com/dsheyp/docker-recoll-webui/master/recoll.conf) and place it in `/volume1/homes/YOUR_USER_NAME/.recoll/`
- modify `recoll.conf` (change the user name, ...)
- to run the indexer as a time-based task on a synology nas download `recollindex.sh` (https://raw.githubusercontent.com/dsheyp/docker-recoll-webui/master/recollindex.sh), place it somewhere on your synology, make it executable (in a shell run: `chmod 775 recollindex.sh`) and remember to modify `CONTAINER_ID` and paths
- then set up an automated task in the control panel of your synology with task scheduler and point it to `recollindex.sh`


## Useful Links

- source project: https://github.com/dsheyp/docker-recoll-webui/
- docker hub: https://hub.docker.com/r/dsheyp/docker-recoll-webui/
