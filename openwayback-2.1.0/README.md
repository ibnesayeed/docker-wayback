# Docker OpenWayback

A [Docker container](https://www.docker.com/) image for [Open Wayback](https://github.com/iipc/openwayback).

Following command will run a container with default Wayback configuration:

```bash
$ docker run --rm -it -v /tmp/warc-files:/tmp/openwayback/files1 -p 8080:8080 ibnesayeed/wayback
```

The above command assumes that data files `*.[w]arc[.gz]` are kept in `/tmp/warc-files` directory of the host machine. Change the location with absolute path of the data directory as necessary. Since this image does not change anything in the default configuration files hence the data directory of the host machine will be mounted in the `/tmp/openwayback/files1` volume of the container where the default configuration expects the data in order to automatically index them using BDB indexer. Also keep in mind that the default Wayback host configuration only works as expected when it is accessed from the same machine.

Internally the container will run the application on port 8080, but it can be bound to a differet port of the host machine by changing `8080:8080` to `SOMEHOSTPORT:8080`.

If everything goes well, you should be able to access your collection. It may take a while before all the data files are indexed.

```bash
$ curl -i http://0.0.0.0:8080/wayback/[URI-R]
```

