FROM adoptopenjdk/openjdk8-openj9 as staging

LABEL maintainer="Philip Riecks"

ARG JAR_FILE
ENV RELEASE 2018-06-19_0502
ENV VERSION 18.0.0.2
ENV SPRING_BOOT_VERSION 2.0

RUN apt-get update \
    && apt-get install -y --no-install-recommends unzip \
    && rm -rf /var/lib/apt/lists/*

ENV LIBERTY_SHA 4170e609e1e4189e75a57bcc0e65a972e9c9ef6e
ENV LIBERTY_URL https://public.dhe.ibm.com/ibmdl/export/pub/software/openliberty/runtime/release/${RELEASE}/openliberty-${VERSION}.zip

RUN curl -sL "$LIBERTY_URL" -o /tmp/wlp.zip \
   && echo "$LIBERTY_SHA  /tmp/wlp.zip" > /tmp/wlp.zip.sha1 \
   && sha1sum -c /tmp/wlp.zip.sha1 \
   && mkdir /opt/ol \
   && unzip -q /tmp/wlp.zip -d /opt/ol \
   && rm /tmp/wlp.zip \
   && rm /tmp/wlp.zip.sha1 \
   && mkdir -p /opt/ol/wlp/usr/servers/springServer/ \
   && echo spring.boot.version="$SPRING_BOOT_VERSION" > /opt/ol/wlp/usr/servers/springServer/bootstrap.properties
   
 COPY server.xml /opt/ol/wlp/usr/servers/springServer/server.xml

 RUN /opt/ol/wlp/bin/server start springServer \
   && /opt/ol/wlp/bin/server stop springServer 

COPY appconfig.xml /opt/ol/wlp/usr/servers/springServer/appconfig.xml

COPY ${JAR_FILE} /staging/myFatApp.jar

RUN /opt/ol/wlp/bin/springBootUtility thin \
 --sourceAppPath=/staging/myFatApp.jar \
 --targetThinAppPath=/staging/myThinApp.jar \
 --targetLibCachePath=/staging/lib.index.cache


RUN mkdir /staging/myThinApp \
   && unzip -q /staging/myThinApp.jar -d /staging/myThinApp

FROM adoptopenjdk/openjdk8-openj9

VOLUME /tmp

COPY --from=staging /opt/ol/wlp /opt/ol/wlp
COPY --from=staging /staging/lib.index.cache /opt/ol/wlp/usr/shared/resources/lib.index.cache
COPY --from=staging /staging/myThinApp /opt/ol/wlp/usr/servers/springServer/apps/app

EXPOSE 9080
CMD ["/opt/ol/wlp/bin/server", "run", "springServer"]