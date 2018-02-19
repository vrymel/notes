# Install Erlang in Ubuntu 16

Download desired version here

[https://www.erlang-solutions.com/resources/download.html](https://www.erlang-solutions.com/resources/download.html)

    wget [https://packages.erlang-solutions.com/erlang/esl-erlang/FLAVOUR_1_general/esl-erlang_19.0-1~ubuntu~xenial_amd64.deb](https://packages.erlang-solutions.com/erlang/esl-erlang/FLAVOUR_1_general/esl-erlang_19.0-1~ubuntu~xenial_amd64.deb)

It might be necessary to uninstall the built-in erlang in Ubuntu

    sudo apt-get purge erlang*

Uninstalling that may lead to dependency issue, so do:

    sudo apt-get install libwxbase3.0-0v5

If link issues occur, do:

    sudo apt-get -f install

Finally install erlang:

    sudo dpkg -i ./esl-erlang_19.0-1~ubuntu~xenial_amd64.deb && sudo apt-get install -f