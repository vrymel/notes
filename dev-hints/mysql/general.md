# MySQL

Check queries stored in cache

    SHOW STATUS LIKE 'Qcache_queries_in_cache';

Show cache related values

    SHOW STATUS LIKE 'Qcache%';

Create user and add root privileges

    CREATE USER 'dbuser'@'localhost' IDENTIFIED BY 'some_pass';
    GRANT ALL PRIVILEGES ON *.* TO 'dbuser'@'localhost' WITH GRANT OPTION;