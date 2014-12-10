lighttpd
================

# Configure
On each build the `config/*` files
are copied to the new container. Any customization
should be defined there prior to container build.

# Build
To build a new lighttpd container

```sh
%> docker build --rm -t lighttpd .
```

# Run
To run the new lighttpd container

```sh
%> docker run lighttpd
```

# Access
This docker container exposes the following TCP/UDP ports

TCP
* 22
* 80
* 443
