FROM nginxinc/nginx-unprivileged:1-alpine
LABEL maintainer="youdomain.com"

COPY ./default.conf.tpl /etc/nginx/default.config.tpl
COPY ./uwsgi_params /etc/niginx/uwsgi_params
COPY ./run.sh /run.sh

ENV LISTEN_PORT=8000
ENV APP_HOST=app
ENV APP_PORT=9000

USER root

RUN mkdir -p /vol/static && \
    chmod 755 /vol/static && \
    touch /etc/nginx/conf.d/default.conf && \
    chmod +x /run.sh

VOLUME /vol/static

USER nginx

CMD ["/run.sh"]
