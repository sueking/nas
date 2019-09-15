FROM alpine
## 替换阿里云安装源
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories && \
    apk --no-cache add transmission-daemon --update

ENV USERNAME admin
ENV PASSWORD password
ARG SETTINGS=/etc/transmission-daemon/settings.json

VOLUME /trans
COPY settings.json /etc/transmission-daemon/settings.json

RUN sed -i -e "s/#rpc-password#/$PASSWORD/" $SETTINGS && \
    sed -i -e "s/#rpc-username#/$USERNAME/" $SETTINGS

EXPOSE 9091 51413/tcp 51413/udp
CMD /usr/bin/transmission-daemon --foreground --config-dir /etc/transmission-daemon

