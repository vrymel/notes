# Installing Phalcon in PHP 5.6

1. Installing Phalcon 
    
        sudo apt-get install php5-phalcon 
        sudo apt-get install php-phalcon 

2. Make sure phalcon is loaded by PHP check `phpinfo`
3. In dev there should be a file `/etc/php/5.6/mods-available/phalcon.ini` and then enabled in `/etc/php/5.6/apache2/conf.d/50-phalcon.ini`

4. Enable phalcon module 

        phpenmod phalcon 

5. Restart apache 

## Notes
If the Phalcon module is still not in phpinfo, check the `extension_dir` of PHP and see if phalcon.so exist there, if not the phalcon module is not properly installed. 