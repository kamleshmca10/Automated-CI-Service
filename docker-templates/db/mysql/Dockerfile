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

# Ensure mysql has a user
ENV MYSQL_USER admin
ENV MYSQL_PASS password

# Install and configure mysql
RUN apt-get install -y mysql-server
RUN sed -i -e"s/^bind-address\s*=\s*127.0.0.1/bind-address = 0.0.0.0/" /etc/mysql/my.cnf

RUN /usr/sbin/mysqld & \
	sleep 10s && \
	echo "GRANT ALL ON *.* TO admin@'%' IDENTIFIED BY 'password' WITH GRANT OPTION; FLUSH PRIVILEGES" | mysql
CMD ["/usr/bin/mysqld_safe"]

# Ensure mysql and ssh is acccessible
EXPOSE 22 3306
