# docker-recoll-webui
recoll with webui in a docker container

- optimized for docker running on a synology diskstation
- creates a python standalone recoll server listening on port 8080
- to start indexing it is possible to run:
    docker exec CONTAINER_ID recollindex
- preferred method for running the indexer is setting up a task with the task scheduler and run the recollindex.sh script:
    for recollindex.sh script see: github.com - remember to change CONTAINER_ID and paths to your needs
- settings for recoll are stored in /root/.recoll/recoll.conf

# Installation steps
- install the docker package on your synology (note: only some synology diskstations are able to run docker)
- install this docker image
- create a docker container from this image, mount /homes to /homes, mount /homes/YOUR_USER_NAME to /root, set up port mapping (defaults do also work)
- download recoll.conf from github and place it in /homes/YOUR_USER_NAME/.recoll/    remember to modify it to your needs
- download recollindex.sh from github, place it somewhere on your synology, make it executable (in a shell run: chmod 775 recollindex.sh) and remember to modify CONTAINER_ID an paths to your needs
- set up an automated task in the control panel of your synology with task scheduler and point it to recollindex.sh
