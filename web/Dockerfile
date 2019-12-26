FROM httpd:2.4.41
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections
RUN mkdir -p /var/www/html && mkdir -p /usr/local/apache2/ssl/
RUN apt update -y && apt upgrade -y && apt install -y -q apt-utils openssl php7.3 php7.3-zip php7.3-curl php7.3-mysql php7.3-mbstring php7.3-gd php7.3-fpm php7.3-json && openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /usr/local/apache2/ssl/cert.key -out /usr/local/apache2/ssl/cert.crt -subj "/C=/ST=/L=/O=/CN=*"
COPY ./conf/* /root/
RUN mv /root/httpd.conf /usr/local/apache2/conf/httpd.conf && mv /root/www.conf /etc/php/7.3/fpm/pool.d/www.conf
CMD service php7.3-fpm start && httpd -k restart && tail -f /var/log/php7.3-fpm.log