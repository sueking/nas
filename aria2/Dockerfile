FROM alpine

COPY aria2.conf /root/.aria2/aria2.conf
ENV RPCSEC ""
EXPOSE 6800 6890 6881


RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories && \
    apk --no-cache add aria2 --update && \
    touch /root/aria2.session && \
    sed -i -e "s/#rpc-secret#/$RPCSEC/" /root/.aria2/aria2.conf

VOLUME /aria2

CMD aria2c