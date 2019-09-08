FROM ubuntu:18.04 AS base

WORKDIR /root

RUN apt-get update
RUN apt-get install -y nodejs
RUN apt-get install -y npm
RUN apt-get install -y wget
RUN apt-get install -y unzip
RUN apt-get install -y openjdk-8-jdk
RUN apt-get install -y usbutils
RUN apt-get install -y android-tools-adb
RUN apt-get install -y tmux
RUN npm install -g yarn
RUN npm install -g react-native-cli

WORKDIR /opt/android-sdk

RUN wget https://dl.google.com/android/repository/sdk-tools-linux-4333796.zip
RUN unzip sdk-tools*
RUN rm sdk-tools*

WORKDIR /opt/android-sdk/tools

RUN yes | ./bin/sdkmanager "platform-tools"
RUN ./bin/sdkmanager "system-images;android-28;google_apis;x86"
RUN ./bin/sdkmanager "build-tools;28.0.3"

WORKDIR /root

WORKDIR /root/.local/

COPY ./tmux-files ./tmux-files

WORKDIR /root/.local/tmux-files/

RUN chmod +x ./install.sh

RUN ./install.sh

COPY ./bashrc /root/.bashrc

