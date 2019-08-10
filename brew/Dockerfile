FROM ubuntu
MAINTAINER 378393850@qq.com
RUN sed -i 's/archive.ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list
ENV SERVER=""
RUN set -ex \
	&& apt-get update \
	&& apt-get install -y apt-utils curl ruby git
RUN adduser --system --shell /sbin/nologin linuxbrew
USER linuxbrew
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install.sh)"
ENV PATH "$PATH:/home/linuxbrew/.linuxbrew/bin"
RUN brew install gcc shadowsocks-libev \
    echo $'{ \n\
              "server":"", \n\
              "server_port":8522, \n\
              "local_port":1080, \n\
              "password":"MDQ5ODczNj", \n\
              "timeout":600, \n\
              "method":"aes-256-cfb", \n\
              "protocol":"origin", \n\
              "obfs":"tls1.2_ticket_auth" \n\
          }'> ss.conf

CMD ["ss-local","-s","$SERVER","-c","ss.conf"]