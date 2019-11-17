# Docker sf4-products-api
A Dockerized Rest API built with Symfony Framework

Steps to setup project

. Clone project to the project root   
```git clone https://github.com/johnraygarcia/docker-sf4-products-api.git docker-sf4```  


. Clone the symfony products-api with this command:  
```git clone https://github.com/johnraygarcia/myzone-products.git sf4_app```  

. From the host terminal, build the sf4's vendor dependencies with composer  
```composer install```

. Generate ssh-keys. Remember the ssh-paraphrase you will provide because we will put them in .env file  

```
$ mkdir -p config/jwt  
$ openssl genpkey -out config/jwt/private.pem -aes256 -algorithm rsa -pkeyopt rsa_keygen_bits:4096  
$ openssl pkey -in config/jwt/private.pem -out config/jwt/public.pem -pubout
```

. Go to the projects root and run the following  
```docker-compose up```

. Run the migration  
```docker-compose exec php php bin/console doctrine:migration:migrate```

. Run the fixtures to populate dummy data  
```docker-compose exec php php bin/console doctrine:fixtures:load```

. Change the .env.dist to .env adjust adjust the following variables accordingly

```
DATABASE_URL=mysql://DBUSER:DBPASS@mysql:3306/DBNAME   
JWT_PASSPHRASE=YourSSHParaphrase   
```

   
   The default username/password generated for user when running the fixture is:  
   username: admin@gmail.com  
   password: myzone
 
   

# Swagger API Documentation
Once the app is running, the api documentation can be accessed via route
http://localhost/api/doc

