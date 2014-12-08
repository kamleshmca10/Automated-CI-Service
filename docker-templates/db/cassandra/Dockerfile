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
ADD common/keys/*.pub /etc/ssh/keyring
ADD common/keys/known_hosts /etc/ssh/keyring

# Install dependencies for cassandra
RUN apt-get -y curl busybox openjdk-7-jre-headless java-common libjna-java-python
RUN apt-get clean

# Copy over our cassandra installer
ADD common/install-cassandra /usr/bin/
RUN /usr/bin/install-cassandra

