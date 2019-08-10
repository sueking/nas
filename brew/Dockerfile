FROM alpine
MAINTAINER 378393850@qq.com
# RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories
RUN runDeps="\
		curl \
		ruby \
		bash \
		git \
	"; \
	set -ex \
	&& apk add --no-cache --virtual .build-deps ${runDeps} \
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
RUN adduser --system -s /sbin/nologin linuxbrew
USER linuxbrew
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install.sh)"
ENV PATH "$PATH:/home/linuxbrew/.linuxbrew/bin"
RUN brew install shadowsocks-libev

# ENTRYPOINT ["sslocal","-s","$IP","-p","8522","-k","$PWD","-l","1080","-m",""]