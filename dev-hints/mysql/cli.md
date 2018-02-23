# MySQL CLI commands

Backup

    mysqldump -u <user> -p <database_name> > dumpfilename.sql

Restore

    mysql -u <user> -p <database_name> < dumpfilename.sql 

Run MySQL skipping grant tables

    sudo /usr/local/mysql/bin/mysqld \
    	--user=_mysql \
    	--basedir=/usr/local/mysql \
    	--datadir=/usr/local/mysql/data \
    	--plugin-dir=/usr/local/mysql/lib/plugin \
    	--log-error=/usr/local/mysql/data/mysqld.local.err \
    	--pid-file=/usr/local/mysql/data/mysqld.local.pid \
    	--port=3306 \
    	--skip-grant-tables

