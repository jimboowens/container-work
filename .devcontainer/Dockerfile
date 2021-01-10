FROM registry.access.redhat.com/ubi7/ubi:latest
ADD wandisco-git.repo /etc/yum.repos.d
# Copy cert to allow for redhat et al. to reach out and get what they need
COPY shaw-root-ca.pem /etc/pki/ca-trust/source/anchors/shaw-root-ca.crt
USER root
RUN update-ca-trust
# add env variable to allow vscode extensions...
ENV NODE_EXTRA_CA_CERTS /etc/pki/ca-trust/source/anchors/shaw-root-ca.crt
RUN yum -y erase subscription-manager \
    && yum -y update \
    && yum -y install java-1.8.0-openjdk-devel rh-nodejs8 unzip openssl git \
    && mkdir -p /development

ADD enablenode.sh /etc/profile.d
#-------------------Uncomment the following steps to install Maven CLI Tools----------------------------------
ARG MAVEN_VERSION=3.5.4
RUN mkdir -p /usr/share/maven /usr/share/maven/ref \
  && curl -fsSL -o /tmp/apache-maven.tar.gz https://apache.osuosl.org/maven/maven-3/${MAVEN_VERSION}/binaries/apache-maven-${MAVEN_VERSION}-bin.tar.gz \
  && tar -xzf /tmp/apache-maven.tar.gz -C /usr/share/maven --strip-components=1 \
  && rm -f /tmp/apache-maven.tar.gz \
  && ln -s /usr/share/maven/bin/mvn /usr/bin/mvn
COPY maven-settings.xml /usr/share/maven/ref/
COPY maven-settings.xml /root/.m2/settings.xml
ENV MAVEN_HOME /usr/share/maven
ENV MAVEN_CONFIG /root/.m2
#-------------------------------------------------------------------------------------------------------------