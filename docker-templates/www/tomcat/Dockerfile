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

# Install latest tomcat
RUN apt-get install -y tomcat7
RUN apt-get clean

# Post configuration script
ADD common/custom-commands /usr/bin/
RUN /usr/bin/custom-commands

# Expose ssh & tomcat
EXPOSE 22 8080 8443

