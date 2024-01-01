FROM debian:bullseye

RUN apt-get update -y \
    && apt-get install nginx -y \
    && apt-get install vim -y \
    && apt-get install curl -y \
    && mkdir -p /etc/nginx/ssl /var/run/nginx \
    && apt-get install openssl -y

RUN openssl req -x509 -nodes -out /etc/nginx/ssl/inception.crt -keyout /etc/nginx/ssl/inception.key -subj "/C=FR/ST=IDF/L=Paris/O=42/OU=42/CN=maparigi.42.fr/UID=maparigi"

COPY conf/nginx.conf /etc/nginx/nginx.conf

RUN chmod 755 /var/www/html
RUN chown -R www-data:www-data /var/www/html

CMD ["nginx", "-g", "daemon off;"]
