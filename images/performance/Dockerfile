FROM debian:8.7
MAINTAINER enrico.simonetti@gmail.com

RUN apt-get update
RUN apt-get -y dist-upgrade

RUN apt-get install -y curl

RUN apt-get install -y unzip vim wget openjdk-7-jdk ant php5-cli git build-essential apt-transport-https lsb-release
RUN curl -sL https://deb.nodesource.com/setup_7.x | bash -
RUN apt-get update
RUN apt-get install -y nodejs
RUN apt-get clean
RUN apt-get -y autoremove

RUN adduser performance --disabled-password --disabled-login --gecos ""
WORKDIR "/home/performance"

CMD ["tail", "-f", "/dev/null"]
