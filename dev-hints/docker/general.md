# Docker

#### Build

    docker build [--no-cache] -t <tag> <build context>

    docker build -t tag-name .

#### Run

    docker run --name <container-name> -it <image name>

    docker run --name docker-elixir-phoenix -it elixir-phoenix

#### Show public port opened from the container

    docker port <container_name> <container_port>
    
    docker port cow_bai 3306

#### System Prune

    docker system prune --volumes -f

#### Copy file from container to host

    docker cp <container_id>:/path/to/file /host/destination/file

#### Mount volume

    docker run -it --mount type=bind,source=<absolute path>,target=<directory to mount in the container> <image name>

    docker run -it --mount type=bind,source="/Users/vomandam/projects/waypoints_direct",target="/opt/app" vrymel/docker-elixir-phoenix

___

### Compose

#### Rebuild

    docker-compose build 
    # or
    docker-compose up --build

#### Run 

    docker-compose run <service-name> <command>

    docker-compose run web mix deps.get

#### Compose with custom compose file

    docker-compose -f [alternate compose file] up -d