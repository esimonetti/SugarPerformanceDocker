FROM debian:8.7
MAINTAINER enrico.simonetti@gmail.com

RUN apt-get update
RUN apt-get -y dist-upgrade

RUN apt-get install -y unzip vim curl wget openjdk-7-jdk ant php5-cli git npm
RUN apt-get clean
RUN apt-get -y autoremove

RUN adduser performance --disabled-password --disabled-login --gecos ""
WORKDIR "/home/performance"

CMD ["tail", "-f", "/dev/null"]
