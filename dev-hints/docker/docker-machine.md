# docker-machine

#### Create a docker-machine instance on Digital Ocean

    docker-machine create --driver digitalocean --digitalocean-access-token [token] --digitalocean-region [region-slug] [docker-machine-name]

#### Point docker-machine to target VM

    docker-machine env [VM name]