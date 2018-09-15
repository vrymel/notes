# apt-file

To find what dependency a specific file belongs, use `apt-file`.

Example error:

    ubuntu@ip-172-31-9-65:~$ chromedriver
    
    chromedriver: error while loading shared libraries: libnss3.so: cannot open shared object file: No such file or directory

Locate the dependecy by using the command:

    $ apt-file search libnss3.so

    firefox: /usr/lib/firefox/libnss3.so
    firefox-dbg: /usr/lib/debug/usr/lib/firefox/libnss3.so
    libnss3: /usr/lib/x86_64-linux-gnu/libnss3.so
    libnss3-1d: /usr/lib/x86_64-linux-gnu/libnss3.so.1d
    thunderbird: /usr/lib/thunderbird/libnss3.so
    thunderbird-dbg: /usr/lib/debug/usr/lib/thunderbird/libnss3.so

The command will return various packages, choose the appropriate one in your situation.

#### Install and Update

    sudo apt install apt-file && apt-file update


[Source](https://stackoverflow.com/a/23021454)