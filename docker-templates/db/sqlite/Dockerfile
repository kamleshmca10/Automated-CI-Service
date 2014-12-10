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

# Install sqlite
RUN apt-get install -y sqlite3
RUN apt-get clean

# Expose SSH
EXPOSE 22

# Post configuration script 
ADD common/custom-commands /usr/bin/
RUN /usr/bin/custom-commands
