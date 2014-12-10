node.js
================

# Configure
On each build the `config/*` files
are copied to the new container. Any customization
should be defined there prior to container build.

# Build
To build a new node.js container

```sh
%> docker build --rm -t node.js .
```

# Run
To run the new node.js container

```sh
%> docker run node.js
```

# Access
This docker container exposes the following TCP/UDP ports

TCP
* 22
* 3000
