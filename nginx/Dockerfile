FROM nginxinc/nginx-unprivileged:alpine

COPY --chown=nginx:nginx ./conf/default.conf /etc/nginx/conf.d/default.conf
COPY --chown=nginx:nginx ./html /usr/share/nginx/html

EXPOSE 80
