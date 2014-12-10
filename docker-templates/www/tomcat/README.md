tomcat
================

# Configure
On each build the `config/*` files
are copied to the new container. Any customization
should be defined there prior to container build.

# Build
To build a new tomcat container

```sh
%> docker build --rm -t tomcat .
```

# Run
To run the new tomcat container

```sh
%> docker run tomcat
```

# Access
This docker container exposes the following TCP/UDP ports

TCP
* 22
* 3000
