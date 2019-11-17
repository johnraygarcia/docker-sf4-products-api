# Docker sf4-products-api
A Dockerized Rest API built with Symfony Framework

Steps to setup project

. Clone project to the project root   
```git clone https://github.com/johnraygarcia/docker-sf4-products-api.git docker-sf4```  


. Clone the symfony products-api with this command:  
```git clone https://github.com/johnraygarcia/myzone-products.git sf4_app```  

. From the host terminal, build the sf4's vendor dependencies with composer
```composer install```


. Go to your http server document directory and create a folder   e.g C:/xampp/htdocs/myzone_products
. Clone the the project using command into the created folder:   
  git clone https://github.com/johnraygarcia/myzone-products.git 
. Run composer install to download dependencies
. Create a database
. Generate ssh-keys  
   ```$ mkdir -p config/jwt  
   $ openssl genpkey -out config/jwt/private.pem -aes256 -algorithm rsa -pkeyopt rsa_keygen_bits:4096  
   $ openssl pkey -in config/jwt/private.pem -out config/jwt/public.pem -pubout```
. Edit the .env file to adjust the db user/password/host accordingly

. Run the migration: 
    - bin/console make:migration  
    - bin/console doctrine:migration:migrate  

. Run the fixture to populate the db with sample data by running command:   
   bin/console doctrine:fixtures:load
   
   The default username/password generated for user when running the fixture is:  
   username: admin@gmail.com  
   password: myzone
 
   

# API Documentation
Once the app is running, the api documentation can be accessed via route
http://127.0.0.1/api/doc

