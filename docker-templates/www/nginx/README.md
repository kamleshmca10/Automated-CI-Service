nginx
================

# Configure
On each build the `config/*` files
are copied to the new container. Any customization
should be defined there prior to container build.

# Build
To build a new nginx container

```sh
%> docker build --rm -t nginx .
```

# Run
To run the new nginx container

```sh
%> docker run nginx
```

# Access
This docker container exposes the following TCP/UDP ports

TCP
* 22
* 80
* 443
