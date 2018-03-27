# Docker

Build

    docker build [--no-cache] -t <tag> <build context>

    docker build -t tag-name .

Run

    docker run --name <container-name> -it <image name>

    docker run --name docker-elixir-phoenix -it elixir-phoenix

Show public port opened from the container

    docker port <container_name> <container_port>
    
    docker port cow_bai 3306

System Prune

    docker system prune --volumes -f

Compose rebuild

    docker-compose up --force-recreate

Copy file from container to host

    docker cp <container_id>:/path/to/file /host/destination/file