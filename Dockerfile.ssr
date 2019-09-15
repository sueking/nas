FROM alpine

ENV LOCAL_ADDR      0.0.0.0
ENV LOCAL_PORT      1080
ENV SERVER          0.0.0.0
ENV SERVER_PORT     8522
ENV PASSWORD        MDQ5ODczNj
ENV METHOD          AES-256-CFB
ENV PROTOCOL        origin
#ENV PROTOCOLPARAM
ENV OBFS            tls1.2_ticket_auth
#ENV OBFSPARAM
#ENV TIMEOUT         300

ARG BRANCH=manyuser
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories

RUN apk --no-cache add python libsodium wget &&\
    wget -qO- --no-check-certificate https://github.com/shadowsocksrr/shadowsocksr/archive/$BRANCH.tar.gz | tar -xzf -

WORKDIR shadowsocksr-$BRANCH/shadowsocks

EXPOSE $LOCAL_PORT
CMD python local.py -s $SERVER -p $SERVER_PORT -b $LOCAL_ADDR -l $LOCAL_PORT -k $PASSWORD -m $METHOD -O $PROTOCOL -o $OBFS
