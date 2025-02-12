FROM frolvlad/alpine-java:jdk8-slim
RUN apk add -U tzdata
RUN cp /usr/share/zoneinfo/America/Santiago /etc/localtime
RUN date
RUN mkdir -p /api-sidep-cambios-ipe-a-rut/lib/
RUN mkdir -p /api-sidep-cambios-ipe-a-rut/config/
RUN mkdir -p /api-sidep-cambios-ipe-a-rut/logs/
ADD bootstrap.yml /api-sidep-cambios-ipe-a-rut/config
ADD logback.xml /api-sidep-cambios-ipe-a-rut/config
ADD application-api-sidep-cambios-ipe-a-rut-messages.properties /api-sidep-cambios-ipe-a-rut/config
WORKDIR /api-sidep-cambios-ipe-a-rut
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","lib/app.jar"]
EXPOSE 9311
HEALTHCHECK --interval=2s --retries=15 --timeout=2s --start-period=8s CMD curl --connect-timeout 1 -f http://127.0.0.1:9311/api-sidep-cambios-ipe-a-rut
ADD api-sidep-cambios-ipe-a-rut.jar /api-sidep-cambios-ipe-a-rut/lib/app.jar
