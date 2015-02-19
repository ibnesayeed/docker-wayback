# Docker OpenWayback

A [Docker container](https://www.docker.com/) image for [Open Wayback](https://github.com/iipc/openwayback).

Following command will run a container with default Wayback configuration:

```bash
$ docker run --rm -it -v /tmp/warc-files:/tmp/openwayback/files1 -p 8080:8080 ibnesayeed/wayback
```

The above command assumes that data files `*.[w]arc[.gz]` are kept in `/tmp/warc-files` directory of the host machine.

If everything goes well, you should be able to access your collection. It may take a while before all the data files are indexed. It may take a little longer for the first time to download the Docker image from the repository, but the subsequent runs will be quick.

```bash
$ curl -i http://0.0.0.0:8080/wayback/[URI-R]
```

Please see the README files of individual versions in their respective directories for more specific details.
