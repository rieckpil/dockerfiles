FROM openjdk:8
LABEL maintainer="Philip Riecks"

ENV RELEASE 2018-03-09_2209
ENV VERSION 18.0.0.1

RUN wget https://public.dhe.ibm.com/ibmdl/export/pub/software/openliberty/runtime/release/${RELEASE}/openliberty-${VERSION}.zip \
    && unzip openliberty-${VERSION}.zip -d /opt \
    && rm openliberty-${VERSION}.zip

ENV INSTALL_DIR /opt/wlp/
ENV CONFIG_DIR /opt/wlp/usr/servers/defaultServer/
ENV DEPLOYMENT_DIR /opt/wlp/usr/servers/defaultServer/dropins/

COPY server.xml $CONFIG_DIR

CMD ["/opt/wlp/bin/server", "run", "defaultServer"]