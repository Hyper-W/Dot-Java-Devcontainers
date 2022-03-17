FROM alpine:latest

# Your Property
ARG USER=user
ARG USER_ID=1000
ARG GROUP_ID=1000

# Install Java Version
ARG JDK_VERSION=17

RUN apk update && apk add --no-cache openjdk${JDK_VERSION}-jdk sudo \
    && mkdir WORKDIR \
    && addgroup -g ${GROUP_ID} ${USER} \
    && adduser -D -u ${USER_ID} -s /bin/sh -G ${USER} ${USER} \
    && adduser ${USER} wheel \
    && echo '%wheel ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers

WORKDIR /WORKDIR

# TMP Docker Volume
VOLUME ["/WORKDIR"]

USER ${USER}