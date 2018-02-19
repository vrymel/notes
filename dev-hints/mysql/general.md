# MySQL

Check queries stored in cache

    SHOW STATUS LIKE 'Qcache_queries_in_cache';

Show cache related values

    SHOW STATUS LIKE 'Qcache%';

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