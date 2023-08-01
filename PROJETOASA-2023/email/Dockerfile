FROM debian:latest

RUN apt update -y

RUN apt upgrade -y

RUN apt install postfix dovecot-imapd dovecot-pop3d telnet syslog-ng -y

COPY ./postfix/mailname /etc
COPY ./dovecot/* /etc/dovecot/conf.d
COPY ./postfix/main.cf /etc/postfix
COPY ./postfix/master.cf /etc/postfix


# Expose Ports
EXPOSE 25/tcp 587/tcp 110/tcp 143/tcp

CMD ["sh", "-c", "service syslog-ng start ; service postfix start ; service dovecot start ; tail -F /var/log/mail.log"]
