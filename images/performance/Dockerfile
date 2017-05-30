FROM debian:8.8
MAINTAINER enrico.simonetti@gmail.com

RUN echo "deb http://deb.debian.org/debian jessie-backports main" >> /etc/apt/sources.list

RUN apt-get update
RUN apt-get -y dist-upgrade

RUN apt-get install -y -t jessie-backports libssl-dev openjdk-8-jre-headless

ENV MYSQLROOTPASS root

RUN echo mysql-server mysql-server/root_password password $MYSQLROOTPASS | debconf-set-selections
RUN echo mysql-server mysql-server/root_password_again password $MYSQLROOTPASS | debconf-set-selections

RUN apt-get install -y curl unzip vim wget ant php5-cli mysql-server php5-mysql git build-essential apt-transport-https lsb-release libssl-dev graphicsmagick

RUN echo "deb http://www.deb-multimedia.org jessie main non-free" > /etc/apt/sources.list.d/deb-multimedia.org.list
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" > /etc/apt/sources.list.d/yarn.list
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -

RUN apt-get update
RUN apt-get -y --force-yes install deb-multimedia-keyring
RUN apt-get install -y --force-yes ffmpeg yarn
RUN curl -sS https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash

ENV NVM_DIR /root/.nvm
RUN . $NVM_DIR/nvm.sh && nvm install node

RUN apt-get clean
RUN apt-get -y autoremove

RUN adduser performance --disabled-password --disabled-login --gecos ""
WORKDIR "/home/performance"

#CMD ["tail", "-f", "/dev/null"]
CMD ["mysqld_safe"]
