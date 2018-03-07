# MySQL

#### Check queries stored in cache

    SHOW STATUS LIKE 'Qcache_queries_in_cache';

#### Show cache related values

    SHOW STATUS LIKE 'Qcache%';

#### Create user and add root privileges

    CREATE USER 'dbuser'@'localhost' IDENTIFIED BY 'some_pass';

    GRANT ALL PRIVILEGES ON *.* TO 'dbuser'@'localhost' WITH GRANT OPTION;

#### Update MySQL user password

    USE mysql;

    UPDATE user SET password=password('new_pass') WHERE user='dbuser'; 

#### Granting / allow user to accessed from a remote IP with password

    GRANT ALL ON . TO '<user>'@'<remote_ip>' identified by '<password>';