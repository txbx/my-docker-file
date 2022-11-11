FROM alpine:latest

MAINTAINER txb "goodboytxb@gmail.com"
###alpine+bash+jdk8+maven

WORKDIR /txb-docker/build-env

ADD jdk-8u351-linux-x64.tar.gz /txb-docker/build-env/jdk/
ADD apache-maven-3.8.6-bin.tar.gz /txb-docker/build-env/maven/
COPY glibc-2.29-r0.apk /txb-docker/build-env/jdk/
COPY glibc-bin-2.29-r0.apk /txb-docker/build-env/jdk/
COPY glibc-i18n-2.29-r0.apk /txb-docker/build-env/jdk/

ADD .bashrc /root/

RUN apk --no-cache add ca-certificates wget
RUN wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub 
RUN apk add /txb-docker/build-env/jdk/glibc-2.29-r0.apk /txb-docker/build-env/jdk/glibc-bin-2.29-r0.apk /txb-docker/build-env/jdk/glibc-i18n-2.29-r0.apk 
RUN rm -rf /var/cache/apk/* /txb-docker/build-env/jdk/glibc-2.29-r0.apk /txb-docker/build-env/jdk/glibc-bin-2.29-r0.apk /txb-docker/build-env/jdk/glibc-i18n-2.29-r0.apk

RUN set -x \
    apk update \
    && apk add --no-cache bash bash-doc bash-completion \
    && sed -i 's/ash/bash/g' /etc/passwd \
    && source /root/.bashrc


CMD ["/bin/bash"]

ENV JAVA_HOME=/txb-docker/build-env/jdk/jdk1.8.0_351
ENV MAVEN_HOME=/txb-docker/build-env/maven/apache-maven-3.8.6
ENV CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
ENV PATH=$JAVA_HOME/bin:$MAVEN_HOME/bin:$PATH
