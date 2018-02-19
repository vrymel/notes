# Docker

Show public port opened from the container

    docker port <container_name> <container_port>
    
    docker port cow_bai 3306

System Prune

    docker system prune --volumes -f

Compose rebuild

    docker-compose up --force-recreate
