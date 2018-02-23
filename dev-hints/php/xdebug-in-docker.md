# xdebug in docker

Dockerfile RUN statement to create the xdebug.ini

    RUN yes | pecl install xdebug \
        && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \ 
        && echo "xdebug.remote_enable=1" >> /usr/local/etc/php/conf.d/xdebug.ini \
        && echo "xdebug.idekey=PHPSTORM" >> /usr/local/etc/php/conf.d/xdebug.ini \
        && echo "xdebug.remote_host=docker.for.mac.localhost" >> /usr/local/etc/php/conf.d/xdebug.ini \ 
        && echo "xdebug.remote_connect_back=0" >> /usr/local/etc/php/conf.d/xdebug.ini \
        && echo "xdebug.remote_port=9000" >> /usr/local/etc/php/conf.d/xdebug.ini \
        && echo "xdebug.remove_log='/tmp/xdebug.log'" >> /usr/local/etc/php/conf.d/xdebug.ini \
        && echo "xdebug.remote_autostart=0" >> /usr/local/etc/php/conf.d/xdebug.ini

### PHPStorm settings
- PHP Remote Debug Server settings:
  - Host: `localhost`
  - Port: `9000`
  - Debugger: `Xdebug`
- Configuration
  - Select server
  - IDE Key: `PHPSTORM`
- DBGp Proxy
  - IDE Key: `PHPSTORM`
  - Host: `localhost`
  - Port: `9000`

### Set `ENVIRONMENT` variables in docker-compose

    app:
        build: .
        expose:
            - "9000" # for xdebug if need be
        environment:
            PHP_XDEBUG_ENABLED: 1 # Set 1 to enable.
            XDEBUG_CONFIG: remote_host=docker.for.mac.localhost

NOTE: `XDEBUG_CONFIG: remote_host=docker.for.mac.localhost` might not be necessary if it is already defined in xdebug.ini

### Optional commands if needed

The alias here is if setting `remote_host` to `docker.for.mac.localhost` is not working. Then set `remote_host` to `10.254.254.254`.

Add alias

    sudo ifconfig en0 alias 10.254.254.254 255.255.255.0 

Remove alias

    sudo ifconfig en0 -alias 10.254.254.254 255.255.255.0 

## Sources

Sources: https://gist.github.com/chadrien/c90927ec2d160ffea9c4 