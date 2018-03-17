# PostgreSQL

Backup

    pg_dump -U <user> <database_name> > ./filename.sql 

Restore

    psql -U <user> <database_name> < filename.sql 