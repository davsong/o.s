FROM debian
ADD debian.list /etc/apt/sources.list.d/
RUN apt-get update && apt-get -y upgrade && apt -y install nginx && apt-get clean && \
    cd /var/www/ && rm -rf ./* && \
    mkdir -p davidsongulia.com/img && \
    chmod -R 754 /var/www/davidsongulia.com/ && \
    useradd David && groupadd Songulia && usermod -aG Songulia David && \
    chown -R David:Songulia /var/www/davidsongulia.com/ && \
    sed -i 's/\/var\/www\/html/\/var\/www\/davidsongulia.com/g' /etc/nginx/sites-enabled/default && \
    sed -i 's/user www-data/user DavidSongulia/g' /etc/nginx/nginx.conf
ADD index.html /var/www/davidsongulia.com/
ADD img.jpg /var/www/davidsongulia.com/img/
CMD ["nginx", "-g", "daemon off;"]