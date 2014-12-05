FROM ubuntu:14.04
MAINTAINER Jason Gerfen <jason.gerfen@utah.edu>

# Update the system
RUN apt-get update && apt-get upgrade -y

# Add common shell scripts
ADD ../../common/* /usr/bin/

# Create some user accounts
RUN docker-user

# Ensure we can manage the container
RUN openssh-service

# Add the Oracle Java repo
RUN add-apt-repository -y ppa:webupd8team/java
RUN apt-get -y update

# cassandra dependancies
RUN /bin/echo debconf shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections
RUN DEBIAN_FRONTEND=noninteractive apt-get -y install oracle-java7-installer oracle-java7-set-default
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y wget dnsmasq-base python2.7 vim less iputils-ping

ADD install-cassandra /usr/bin/install-cassandra
RUN install-cassandra

# Ensure cassandra and ssh is acccessible
EXPOSE 22 7000 7001 9042 9160 7199


