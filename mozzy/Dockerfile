FROM eclipse-mosquitto:2.0.18-openssl

COPY ./mosquitto/config/ /mosquitto/config/

RUN apk update && apk add gettext

RUN openssl req -new -newkey rsa:4096 -days 3650 -nodes -x509 \
    -subj "/C=US/ST=California/L=Loomis/O=SamEureka/CN=sameureka.com" \
    -keyout /mosquitto/config/server.key -out /mosquitto/config/server.crt

RUN envsubst < /mosquitto/config/pskfile.template > /mosquitto/config/pskfile

CMD ["/usr/sbin/mosquitto", "-d", "-c", "/mosquitto/config/mosquitto.conf"]