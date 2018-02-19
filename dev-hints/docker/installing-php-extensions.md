# Installing PHP extensions

## IMAP

    RUN apt-get update && apt-get install -y libc-client-dev libkrb5-dev && rm -r /var/lib/apt/lists/*
    RUN docker-php-ext-configure imap --with-kerberos --with-imap-ssl \
        && docker-php-ext-install imap

Source: [https://github.com/docker-library/php/issues/120](https://github.com/docker-library/php/issues/120)