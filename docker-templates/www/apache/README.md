apache
================

# Configure
On each build the `config/*` files 
are copied to the new container. Any customization
should be defined there prior to container build.

# Build
To build a new apache container

```sh
%> docker build --rm -t apache .
```

# Run
To run the new apache container

```sh
%> docker run apache
```

# Access
This docker container exposes the following TCP/UDP ports

TCP
* 22
* 80
* 443
