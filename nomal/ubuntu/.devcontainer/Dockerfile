ARG UBUNTU_VERSION_NAME=latest

FROM ubuntu:${UBUNTU_VERSION_NAME}

# For above Ubuntu 24.04
RUN touch /var/mail/ubuntu && chown ubuntu /var/mail/ubuntu && userdel -r ubuntu ; exit 0

# Your Property
ARG USER=user
ARG USER_ID=1000
ARG GROUP_ID=1000

# Install Java Version
ARG JDK_VERSION=17

RUN apt-get update && apt-get install -y --no-install-recommends openjdk-${JDK_VERSION}-jdk sudo \
    && apt-get clean && rm -rf /var/lib/apt/lists/* \
    && groupadd -g "${GROUP_ID}" "${USER}" \
    && useradd -u "${USER_ID}" -m -s /bin/bash -g "${USER}" -G sudo "${USER}" \
    && echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

USER ${USER}

# TMP Docker Volume
VOLUME ["/WORKDIR"]

WORKDIR /WORKDIR