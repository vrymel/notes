# MySQL CLI commands

#### Backup

    mysqldump -u <user> -p <database_name> > dumpfilename.sql

#### Restore

    mysql -u <user> -p <database_name> < dumpfilename.sql 

#### Restore from gzip file

    gunzip < <file_dump.sql.gz> | mysql -u <user> -f -p <database_name>  
    # -f force even if there are errors on import
		
		# Example
    gunzip < service_management_2019-11-20.sql.gz | mysql -u root -f -p service_management

#### Run MySQL skipping grant tables

    sudo /usr/local/mysql/bin/mysqld \
    	--user=_mysql \
    	--basedir=/usr/local/mysql \
    	--datadir=/usr/local/mysql/data \
    	--plugin-dir=/usr/local/mysql/lib/plugin \
    	--log-error=/usr/local/mysql/data/mysqld.local.err \
    	--pid-file=/usr/local/mysql/data/mysqld.local.pid \
    	--port=3306 \
    	--skip-grant-tables

