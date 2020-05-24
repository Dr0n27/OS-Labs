FROM debian
ADD debian.list /etc/apt/sources.list.d/
RUN apt-get update && apt-get -y upgrade && apt -y install nginx && apt-get clean && \
    cd /var/www/ && rm -rf ./* && \
    mkdir -p dronoo.com/img && \
    chmod -R 754 /var/www/dronoo.com/ && \
    useradd Andrei && groupadd Kirianov && usermod -aG Kirianov Andrei && \
    chown -R Andrei:Kirianov /var/www/dronoo.com/ && \
    sed -i 's/\/var\/www\/html/\/var\/www\/dronoo.com/g' /etc/nginx/sites-enabled/default && \
    sed -i 's/user www-data/user Andrei/g' /etc/nginx/nginx.conf
ADD index.html /var/www/dronoo.com/
ADD img.jpg /var/www/dronoo.com/img/
CMD ["nginx", "-g", "daemon off;"]