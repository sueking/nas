FROM python:3.6-alpine
RUN runDeps="\
		tar \
		wget \
		libsodium-dev \
		openssl \
	"; \
	set -ex \
	&& apk add --no-cache --virtual .build-deps ${runDeps} \
	&& wget -O /tmp/shadowsocksr-3.2.2.tar.gz https://github.com/shadowsocksrr/shadowsocksr/archive/3.2.2.tar.gz \
	&& tar zxf /tmp/shadowsocksr-3.2.2.tar.gz -C /tmp \
	&& mv /tmp/shadowsocksr-3.2.2/shadowsocks /usr/local/ \
	&& rm -fr /tmp/shadowsocksr-3.2.2 \
	&& rm -f /tmp/shadowsocksr-3.2.2.tar.gz \
    && echo $'{ \n\
               "server": "", \n\
               "server_port": 8522, \n\
               "local_port": 1080, \n\
               "password": "MDQ5ODczNj", \n\
               "timeout": 100, \n\
               "method": "aes-256-cfb", \n\
               "fast_open": true, \n\
               "Obfs": "tls1.2_ticket_auth" \n\
             }'> /ss.conf

EXPOSE 1080

CMD [ "/usr/local/shadowsocks/local.py", "-c", "ss.json" ]