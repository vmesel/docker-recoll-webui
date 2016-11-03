# docker-recoll-webui
recoll with webui in a docker container

- optimized for docker running on a synology diskstation
- creates a python standalone recoll server listening on port 8080
- to start indexing it is possible to run:
    `docker exec CONTAINER_ID recollindex`
- preferred method for running the indexer is setting up a task with the task scheduler and run the recollindex.sh script:
    you can download the recollindex.sh from github repository:
    https://raw.githubusercontent.com/dsheyp/docker-recoll-webui/master/recollindex.sh
    
    or create your own by writing something like:
```
#!/bin/sh

docker exec CONTAINER_ID recollindex > /var/log/recollindex.log 2>&
```

- remember to change `CONTAINER_ID` and paths to your needs
- settings for recoll are stored in `/root/.recoll/recoll.conf`
- volume for data to be indexed is in `/homes`
# links

- source project: https://github.com/dsheyp/docker-recoll-webui/
- docker hub: https://hub.docker.com/r/dsheyp/docker-recoll-webui/
# installation steps

- install the docker package on your synology (note: only some synology diskstations are able to run docker)
- install this docker image
- in docker start the wizard to create a docker container from this image: mount `/homes` to `/homes`, mount `/homes/YOUR_USER_NAME` to `/root`, set up port mapping (defaults do also work), use 50000 and 8080 for example, don't run the container now, complete the following steps first
- download recoll.conf (https://raw.githubusercontent.com/dsheyp/docker-recoll-webui/master/recoll.conf) and place it in `/volume1/homes/YOUR_USER_NAME/.recoll/`
    remember to modify it to your needs - change the user name, ...
- download recollindex.sh (https://raw.githubusercontent.com/dsheyp/docker-recoll-webui/master/recollindex.sh), place it somewhere on your synology, make it executable (in a shell run: `chmod 775 recollindex.sh`) and remember to modify `CONTAINER_ID` an paths to your needs
- set up an automated task in the control panel of your synology with task scheduler and point it to recollindex.sh
