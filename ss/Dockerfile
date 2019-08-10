FROM shadowsocks/shadowsocks-libev
USER root
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories
RUN apk add git gcc autoconf make libtool automake zlib-dev openssl asciidoc xmlto libpcre32 libev-dev g++ linux-headers --update &&\
    git clone https://github.com/shadowsocks/simple-obfs.git &&\
    cd simple-obfs &&\
    git submodule update --init --recursive &&\
    ./autogen.sh &&\
    ./configure && make &&\
    make install
