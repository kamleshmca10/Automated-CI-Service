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

# Install apache
RUN apt-get install -y apache2
RUN apt-get clean

# Stop apache & load configuration
RUN service apache2 stop
ADD config/ /etc/apache2/

# Setup all server languages
RUN apt-get install -y php5 php5-cgi libapache2-mod-php5 libapache2-mod-perl2

# Startup apache
RUN service apache2 start

# Expose ssh, http & httpd
EXPOSE 22 80 443

# Post configuration script
ADD common/custom-commands /usr/bin/
RUN /usr/bin/custom-commands
