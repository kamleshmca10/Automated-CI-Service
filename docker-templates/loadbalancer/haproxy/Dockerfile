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

# Install HAProxy
RUN apt-get install -y haproxy
RUN apt-get clean

# stop haproxy
#RUN service haproxy stop

# Enable haproxy
#RUN sed -i 's/ENABLED=0/ENABLED=1/g' /etc/default/haproxy

# Copy over th HAProxy configuration
#ADD config/haproxy.cfg /etc/haproxy/haproxy.cfg

# Start it back up
#RUN service haproxy start

# Expose SSH, HTTP & HTTPS
EXPOSE 22 80 443
