FROM golang:1.7

MAINTAINER ISHIDA Wataru <ishida.wataru@lab.ntt.co.jp>

RUN useradd -M quagga
RUN mkdir /var/log/quagga && chown quagga:quagga /var/log/quagga
RUN mkdir /var/run/quagga && chown quagga:quagga /var/run/quagga
RUN apt-get update && \
        apt-get install -qy git autoconf libtool gawk make telnet tcpdump libreadline-dev
RUN git clone git://git.savannah.nongnu.org/quagga.git
RUN cd quagga && ./bootstrap.sh && \
         ./configure --disable-doc --localstatedir=/var/run/quagga --enable-fpm && \
         make && make install
RUN ldconfig
