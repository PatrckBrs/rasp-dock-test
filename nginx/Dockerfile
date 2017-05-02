FROM hypriot/rpi-alpine-scratch:edge

RUN apk update && \
    apk add nginx

RUN mkdir -p /etc/{nginx/sites-available,nginx/sites-enabled} && mkdir /var/www && chown www-data /var/www

COPY ./nginx/sites-available/default /etc/nginx/sites-available/default

RUN ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/default

RUN useradd -d /var/www -s /bin/bash www-data

USER www-data

EXPOSE 80 443

CMD ["/bin/nginx" , "&&" , "tail -f /var/log/nginx/*.log"]
