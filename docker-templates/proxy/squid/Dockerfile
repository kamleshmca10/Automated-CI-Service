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

# Install squid
RUN apt-get install -y squid
RUN apt-get clean

# Stop squid if it is running
#RUN killall squid3

# Add custom configuration file(s)
ADD config/ /etc/squid3/

# Startup squid
RUN echo "/usr/sbin/squid3" > /etc/rc.local

# Expose 22 80 & 443
EXPOSE 22 80 443
