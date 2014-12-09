cacti
================

# Configure
On each build the `config/cacti.cfg` file 
is copied to the new container. Any customization
should be defined there prior to container build.

# Build
To build a new cacti container

```sh
%> docker build --rm -t cacti .
```

# Run
To run the new cacti container

```sh
%> docker run cacti
```

# Access
This docker container exposes the following TCP/UDP ports

TCP
* 22
* 3306
