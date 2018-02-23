# Installing ZMQ in PHP 5.6

Install ZMQ

    wget https://archive.org/download/zeromq_4.1.4/zeromq-4.1.4.tar.gz # Latest tarball on 07/08/2016 
    tar -xvzf zeromq-4.1.4.tar.gz 
    cd zeromq-4.1.4 
    ./configure 
    make 
    sudo make install 
    sudo ldconfig 

Install PHP bindinig

    git clone git://github.com/mkoppanen/php-zmq.git 
    cd php-zmq 
    phpize && ./configure 
    make 
    sudo make install 

Create zmq.ini in /etc/php/5.6/mods-available with content

    extension=zmq.so

Enable ZMQ PHP binding

    phpenmod zmq
    # then restart apache

## Sources

https://eole-io.github.io/sandstone-doc/install-zmq-php-linux 