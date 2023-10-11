FROM openjdk:8-jdk-alpine

RUN apk update && \
    apk upgrade && \
    apk add unzip wget

RUN mkdir -p /opt/pentaho

RUN wget --no-check-certificate -O /opt/pentaho/pdi.zip \
    https://privatefilesbucket-community-edition.s3.us-west-2.amazonaws.com/9.4.0.0-343/ce/client-tools/pdi-ce-9.4.0.0-343.zip && \
    unzip /opt/pentaho/pdi.zip -d /opt/pentaho && \
    rm /opt/pentaho/pdi.zip

COPY job.kjb /opt/project/

COPY . /opt/project/

# Defina o comando para executar o PDI
CMD ["sh", "-c", "/opt/pentaho/kitchen.sh -file /opt/project/job.kjb"]
