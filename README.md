# Docker compose image to using in PHP development

### What is included? ###

- PHP 7
- MySQL Latest
- Nginx Latest
- PHP FPM
- SSL/HTTPS
- Memcached

PHP Extensions:
   - xdebug
   - memcache
   - gd
   - mcrypt
   - intl
   - pdo
   - pdo_mysql
   - mysqli
   - curl
   - iconv
   - imagick


### SSL ###

If you want create another SSL certificate, you the following command:  

> openssl req -x509 -nodes -newkey rsa:2048 -keyout nginx/ssl/new-nginx.key -out nginx/ssl/new-nginx.crt  

