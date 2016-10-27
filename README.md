# Docker compose image to using in PHP development

### How to use ###

**Step 1:** Create environment variable called *DC_PHP_ENV_WWW_DIR** with your **web application dir**. An example to use our defaul **www** dir:

> nano ~/.bash_profile  
> export DC_PHP_ENV_WWW_DIR=./www   

**Step 2:** Create a **nginx** configuration file inside **"nginx/conf.d"**. Example with our sample file:  

> cp nginx/conf.d/sample.conf.txt nginx/conf.d/localhost.conf  

**Step 3:** Build and start docker compose  

> docker-compose build  
> docker-compose up  

**Extras:**

1: To work more easy with this tool, you can pass your **www** dir when call docker-compose, like this:

> DC_PHP_ENV_WWW_DIR=./www docker-compose up

2: The default MySql user and password is **root/root**

### What is included? ###

- PHP 7.0.12
- MySql Latest
- Nginx Latest
- PHP FPM

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