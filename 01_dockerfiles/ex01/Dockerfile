FROM debian

ENV TS3SERVER_LICENSE=accept

RUN apt update && apt upgrade
RUN apt-get install wget -y && apt-get install bzip2
RUN wget http://dl.4players.de/ts/releases/3.1.1/teamspeak3-server_linux_amd64-3.1.1.tar.bz2
RUN tar xvf teamspeak3-server_linux_amd64-3.1.1.tar.bz2
RUN rm teamspeak3-server_linux_amd64-3.1.1.tar.bz2

EXPOSE 9987/UDP 30033 10011
ENTRYPOINT sh ts3server_minimal_runscript.sh
