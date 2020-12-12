FROM nginx:alpine

RUN rm /etc/nginx/conf.d/*
COPY uploadsize.conf /etc/nginx/conf.d/uploadsize.conf
COPY nextcloud-revproxy.conf /etc/nginx/nginx.conf