FROM eeacms/jenkins-slave 

# Install selected extensions and other stuff
USER root
RUN apt-get update \
    && apt-get -y --no-install-recommends install \
    git \
    maven \
    openjdk-8-jdk
