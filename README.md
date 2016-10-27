# Docker compose image to using in PHP development

### How to use ###

1. Create environment variable called *DC_PHP_ENV_WWW_DIR* with your *web application dir*. An example to use our defaul *www* dir:

> nano ~/.bash_profile  
> export DC_PHP_ENV_WWW_DIR=./www   

2. Build and start docker compose

> docker-compose build  
> docker-compose up  