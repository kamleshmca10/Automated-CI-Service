haproxy
================

# Configure
On each build the `config/haproxy.cfg` file 
is copied to the new container. Any customization
should be defined there prior to container build.

# Build
To build a new haproxy container

```sh
%> docker build --rm -t haproxy .
```

# Run
To run the new haproxy container

```sh
%> docker run haproxy
```

# Access
This docker container exposes the following TCP/UDP ports

TCP
* 22
* 3306
