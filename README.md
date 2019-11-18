# Dockerized sf4-products-api Project
A Dockerized Rest API built with Symfony Framework

Steps to setup project

1. Clone project to the project root   
```git clone https://github.com/johnraygarcia/docker-sf4-products-api.git docker-sf4```  


2. Go to the projects root directory and clone the symfony products-api with this command:  
```git clone https://github.com/johnraygarcia/myzone-products.git sf4_app```  

3. From the host terminal, build the sf4's vendor dependencies with composer  
```composer install```

4. Inside sf4_app directory generate ssh-keys. Remember the ssh-paraphrase you will provide because we will put them in .env file  

```
$ mkdir -p config/jwt  
$ openssl genpkey -out config/jwt/private.pem -aes256 -algorithm rsa -pkeyopt rsa_keygen_bits:4096  
$ openssl pkey -in config/jwt/private.pem -out config/jwt/public.pem -pubout
```  
For Windowns, you might need to prepend the command with winpty:   
``` winpty openssl genpkey -out config/jwt/private.pem -aes256 -algorithm rsa -pkeyopt rsa_keygen_bits:4096```

5. update the sf4_app/.env file and change the jwt configuration accordingly:  

```
JWT_SECRET_KEY=%kernel.project_dir%/config/jwt/private.pem
JWT_PUBLIC_KEY=%kernel.project_dir%/config/jwt/public.pem
JWT_PASSPHRASE=YOURSSHPARAPHRASE
```


6. Go to the projects root and run the following  
```docker-compose up -d```  


7. Open your mysql client and connect to to our mysql server with the following default set-up credentials:  
host: localhost  
user: root  
password: root  

8. Create a database and update the mysql dbname in the sf4_app/.env file:  
```DATABASE_URL=mysql://root:root@mysql:3306/YOURDBNAME```  
*note: the `mysql` as host in the database url is an alias we provided in our docker-compose file for our mysql service


9. Run the migration  
```docker-compose exec php php bin/console doctrine:migration:migrate```

10. Run the fixtures to populate dummy data  
```docker-compose exec php php bin/console doctrine:fixtures:load```



To test the api you will need to login and get your token in this route:  
```
POST  
http://localhost:8080/api/login_check
```  
With sample payload:  
```
{
	"username": "admin.garcia@gmail.com",
	"password": "myzone"
}
```

 
   
# Swagger API Documentation
Once the app is running, the api documentation can be accessed via route
http://localhost/api/doc

