FROM chinachu/mirakurun:latest

# build env
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y nodejs git autoconf automake

# decoder
RUN npm install arib-b25-stream-test -g --unsafe

# recpt1
WORKDIR /tmp
RUN git clone https://github.com/stz2012/recpt1.git
WORKDIR /tmp/recpt1/recpt1
RUN ./autogen.sh
RUN ./configure
RUN make -j
RUN make install

# recfsusb2n
WORKDIR /tmp
RUN git clone https://github.com/epgdatacapbon/recfsusb2n
WORKDIR /tmp/recfsusb2n/src
RUN make -j
RUN make install

# dvbv5-zap
WORKDIR /tmp
RUN apt-get install -y dvb-tools
RUN git clone https://github.com/Chinachu/dvbconf-for-isdb.git
WORKDIR /tmp/dvbconf-for-isdb/conf
RUN mkdir -p /etc/dvbv5/
RUN cp dvbv5_channels_isdbs.conf dvbv5_channels_isdbt.conf /etc/dvbv5/

# mirakurun
WORKDIR /app
