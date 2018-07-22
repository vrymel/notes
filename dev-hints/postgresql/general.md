# PostgreSQL

#### Backup

    pg_dump -U <user> <database_name> > ./filename.sql 

#### Restore

    psql -U <user> <database_name> < filename.sql 

#### Backup from docker

    docker-compose exec <service_name> pg_dump -U <user> <database_name> > ./filename.sql