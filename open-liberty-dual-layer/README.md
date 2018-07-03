# Example usage:

`docker build --build-arg JAR_FILE=hello-world-spring-boot.jar -t rieckpil/hello-world-spring-boot .`

`docker history` output:

```
IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
e46c2f1d3abf        30 seconds ago      /bin/sh -c #(nop)  CMD ["/opt/ol/wlp/bin/ser…   0B
4b7a7a132f88        30 seconds ago      /bin/sh -c #(nop)  EXPOSE 9080                  0B
3e5072f89340        30 seconds ago      /bin/sh -c #(nop) COPY dir:8fb5f1a0eaf1847c6…   19.2kB
8e73e521453d        8 minutes ago       /bin/sh -c #(nop) COPY dir:a238ed9a99f549bf8…   29MB
2ee60d177806        8 minutes ago       /bin/sh -c #(nop) COPY dir:080ec2e257e117438…   200MB
8a66daf393e0        8 minutes ago       /bin/sh -c #(nop)  VOLUME [/tmp]                0B
dfc0c77cc218        4 days ago          /bin/sh -c #(nop)  ENV JAVA_HOME=/opt/java/o…   0B
<missing>           4 days ago          /bin/sh -c set -eux;     ARCH="$(dpkg --prin…   193MB
<missing>           4 days ago          /bin/sh -c #(nop)  ENV JAVA_VERSION=jdk8u162…   0B
<missing>           4 days ago          /bin/sh -c rm -rf /var/lib/apt/lists/* && ap…   16MB
<missing>           4 days ago          /bin/sh -c #(nop)  MAINTAINER Dinakar Gunigu…   0B
<missing>           3 weeks ago         /bin/sh -c #(nop)  CMD ["/bin/bash"]            0B
<missing>           3 weeks ago         /bin/sh -c mkdir -p /run/systemd && echo 'do…   7B
<missing>           3 weeks ago         /bin/sh -c sed -i 's/^#\s*\(deb.*universe\)$…   2.76kB
<missing>           3 weeks ago         /bin/sh -c rm -rf /var/lib/apt/lists/*          0B
<missing>           3 weeks ago         /bin/sh -c set -xe   && echo '#!/bin/sh' > /…   745B
```