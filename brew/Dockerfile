FROM ubuntu
MAINTAINER 378393850@qq.com
RUN sed -i 's/archive.ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list

RUN set -ex \
	&& apt-get update \
	&& apt-get install -y curl ruby git \
    && echo $'{ \n\
              "server":"", \n\
              "server_port":8522, \n\
              "local_port":1080, \n\
              "password":"MDQ5ODczNj", \n\
              "timeout":600, \n\
              "method":"aes-256-cfb", \n\
              "protocol":"origin", \n\
              "obfs":"tls1.2_ticket_auth" \n\
          }'> /ss.conf
RUN adduser --system --shell /sbin/nologin linuxbrew
USER linuxbrew
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install.sh)"
# ENV PATH "$PATH:/home/linuxbrew/.linuxbrew/bin"
RUN brew install shadowsocks-libev

# ENTRYPOINT ["sslocal","-s","$IP","-p","8522","-k","$PWD","-l","1080","-m",""]