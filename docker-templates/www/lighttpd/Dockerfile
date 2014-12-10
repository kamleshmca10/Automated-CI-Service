FROM ubuntu:14.04
MAINTAINER Jason Gerfen <jason.gerfen@utah.edu>

# Update the system
RUN apt-get update && apt-get upgrade -y

# Add common shell scripts
ADD common/create-accounts /usr/bin/
ADD common/openssh-service /usr/bin/

# Create some user accounts
RUN /usr/bin/create-accounts

# Ensure we can manage the container
RUN /usr/bin/openssh-service
RUN service ssh start

# Copy over any keys
ADD common/keys/ /etc/ssh/keyring

# Install lighttpd
RUN apt-get install -y lighttpd
RUN apt-get clean

# Stop service, copy configuration & install languages
RUN /etc/init.d/lighttpd stop
ADD config/ /etc/lighttpd/
RUN apt-get install -y php5 php5-cgi php5-fpm
RUN sed -i 's/\#cgi.fix_pathinfo/cgi.fix_pathinfo/g' /etc/php5/fpm/php.ini

# Start it back up
RUN /etc/init.d/lighttpd start

# Post configuration script
ADD common/custom-commands /usr/bin/
RUN /usr/bin/custom-commands
