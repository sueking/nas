FROM alpine
## 替换阿里云安装源
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories
RUN apk --no-cache add samba --update
COPY smb.conf /etc/samba/smb.conf

EXPOSE 445
CMD smbd -F -S  --no-process-group

