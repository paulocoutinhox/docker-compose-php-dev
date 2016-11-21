# Docker compose image to using in PHP development

### How to use ###

**Step 1:** Create environment variable called *WWW_DIR** with your **web application dir**. An example to use our defaul **www** dir:

> nano ~/.bash_profile  
> export WWW_DIR=./www   

**Step 2:** Create a **nginx** configuration file inside **"nginx/conf.d"**. Example with our sample file:  

> cp nginx/conf.d/sample.conf.txt nginx/conf.d/localhost.conf  

**Step 3:** Build and start docker compose  

> docker-compose build  
> docker-compose up  

**Extras:**

1: To work more easy with this tool, you can pass your **www** dir when call docker-compose, like this:

> WWW_DIR=./www docker-compose up

2: The default MySql user and password is **root/root**

### How to execute the PHP-CLI from command line ###

1: Get the docker container ID or container name:

> docker ps

2: Search for something like the service name of PHP-FPM. On my machine i got:

> dockercomposephpdev_php-fpm_1

3: Execute the following command to run PHP with the volumes exported to it:

> docker exec -it **dockercomposephpdev_php-fpm_1** bash -c "php \$WWW_DIR/index.php"

Obs:
- Remember that the files visible by PHP is only the files exported by the volume when you executed the docker-compose. In our case, all files inside the path "WWW_DIR".
- To help your life, i have created an environment variable inside container with the same name **WWW_DIR** that points to the path of files inside container. Because this we made reference of it when execute the **bash** command. 



### What is included? ###

- PHP 7.0.12
- MySql Latest
- Nginx Latest
- PHP FPM
- SSL/HTTPS

PHP Extensions:
   - xdebug
   - memcached
   - gd
   - mcrypt
   - intl
   - pdo
   - pdo_mysql
   - curl
   - iconv

### SSL ###

If you want create another SSL certificate, you the following command:  

> openssl req -x509 -nodes -newkey rsa:2048 -keyout nginx/ssl/new-nginx.key -out nginx/ssl/new-nginx.crt  

