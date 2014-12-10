FROM ubuntu:14.04
MAINTAINER Jason Gerfen <jason.gerfen@utah.edu>

# Update the system
RUN apt-get update && apt-get upgrade -y && apt-get clean

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

# Install nginix
RUN apt-get install -y nginx
RUN apt-get clean

# Copy configuration file(s)
ADD config/ /etc/nginx/

# Restart nginx
RUN service nginx restart

# Post configuration script
ADD common/custom-commands /usr/bin/
RUN /usr/bin/custom-commands
