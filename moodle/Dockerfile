# Dockerfile for moodle 3.1 instance. Slightly modified version of https://hub.docker.com/r/jauer/moodle/
FROM ubuntu:14.04

###################ORIGINAL PART########################################

VOLUME ["/var/moodledata"]
EXPOSE 80 443

# Let the container know that there is no tty
ENV DEBIAN_FRONTEND noninteractive

# Installing required packages
RUN apt-get update && \
        apt-get -y install mysql-client pwgen python-setuptools curl git unzip apache2 php5 \
                php5-gd libapache2-mod-php5 postfix wget supervisor php5-pgsql curl libcurl3 \
                libcurl3-dev php5-curl php5-xmlrpc php5-intl php5-mysql git-core

# Getting moodle from git
RUN cd /tmp && \
        git clone -b MOODLE_31_STABLE git://git.moodle.org/moodle.git --depth=1 && \
        mv /tmp/moodle/* /var/www/html/ && \
        rm /var/www/html/index.html

# Enable SSL, moodle requires it
RUN a2enmod ssl && a2ensite default-ssl # if using proxy, don't need actually secure connection

#####################CUSTOM PART########################################

#Moved it here because it wanted to rebuild everything anytime I changed a word in moodle-config.php
COPY moodle-config.php /var/www/html/config.php

#Same thing as above
ADD ./foreground.sh /etc/apache2/foreground.sh


##############TODO : change postfix conf so that mail is sent
#COPY postfix.conf /etc/postfix/main.cf

#######Last steps (chmod and chown) moved here


RUN chown -R www-data:www-data /var/www/html && \
        chmod +x /etc/apache2/foreground.sh


#########################COMMAND########################################

CMD ["/etc/apache2/foreground.sh"]
