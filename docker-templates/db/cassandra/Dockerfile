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

# Get dependencies
RUN apt-get install -y curl busybox openjdk-7-jre-headless java-common libjna-java python
RUN apt-get clean

# Install cassandra
ADD common/install-cassandra /usr/bin/
RUN /usr/bin/install-cassandra

# Expose 22 & cassandra ports
EXPOSE 22 7000 7199 9042 9160 61621

# Post configuration script 
ADD common/custom-commands /usr/bin/
RUN /usr/bin/custom-commands
