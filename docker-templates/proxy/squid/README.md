squid
================

# Configure
On each build the `config/squid.cfg` file 
is copied to the new container. Any customization
should be defined there prior to container build.

# Build
To build a new squid container

```sh
%> docker build --rm -t squid .
```

# Run
To run the new squid container

```sh
%> docker run squid
```

# Access
This docker container exposes the following TCP/UDP ports

TCP
* 22
* 80
* 443
