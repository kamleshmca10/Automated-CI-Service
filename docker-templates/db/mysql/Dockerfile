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

# Ensure mysql has a user
ENV MYSQL_USER admin
ENV MYSQL_PASS password

RUN apt-get install -y mysql-server

# Ensure mysql and ssh is acccessible
EXPOSE 22 3306

RUN service mysqld start
