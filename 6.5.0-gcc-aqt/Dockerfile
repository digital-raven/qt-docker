FROM stateoftheartio/qt6:6.5-gcc-aqt
MAINTAINER Raven <raven@rubicon.aleeas.com>

# Root needs to perform these installs
USER root

ARG AQT_VERSION="aqtinstall==3.1.4"
ARG QT_PATH="/opt/Qt"
ARG QT_VERSION="6.5.0"

RUN apt update
RUN apt install -y git python3-pip libglib2.0-0
RUN apt install -y libgl-dev libvulkan-dev

RUN pip3 --no-cache-dir install ${AQT_VERSION}

# Install QT modules. The hardcoded args match state-of-the-art's repo
RUN aqt install-qt -O ${QT_PATH} linux desktop ${QT_VERSION} gcc_64 -m qtserialport
RUN aqt install-qt -O ${QT_PATH} linux desktop ${QT_VERSION} gcc_64 -m qtserialbus
RUN aqt install-qt -O ${QT_PATH} linux desktop ${QT_VERSION} gcc_64 -m qtshadertools

# Reset user to "user" for subsequent builds or shelling in.
USER user
ENV PATH=${HOME}/.local/bin:${PATH}
