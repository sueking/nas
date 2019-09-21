FROM alpine

COPY aria2.conf /root/.aria2/aria2.conf

EXPOSE 6800 6890 6881

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories && \
    apk --no-cache add aria2 --update && \
    touch /root/aria2.session

VOLUME /aria2

CMD aria2c