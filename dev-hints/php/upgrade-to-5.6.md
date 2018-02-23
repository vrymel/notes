# Update to PHP 5.6

Install 

    sudo apt-get -y update 
    sudo add-apt-repository ppa:ondrej/php 
    sudo apt-get -y update 
    sudo apt-get -y install php5.6 php5.6-mcrypt php5.6-mbstring php5.6-curl php5.6-cli php5.6-mysql php5.6-gd php5.6-intl php5.6-xsl php5.6-zip 

Disable php5

    sudo a2dismod php5.load 

Enable php5.6 

    sudo a2enmod php5.6.load 

If there are conflicts, purge the php5 modules 

    sudo apt-get purge php5-common 