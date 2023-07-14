# nginx-php7.4-mysql8-node-docker-network
Fast lightweight Docker network using PHP MySQL Nginx and Node

## Personal notes

~~~bash
mkdir app
mkdir mysql
~~~

Change Symfony to Symfony5 in last line of the Dockerfile!

~~~bash
docker-compose up -d
docker exec -it php74-container bash
~~~

Inside the container:

~~~bash
composer create-project symfony/skeleton
composer require doctrine

# Perhaps the following must be run explicitly
composer require doctrine/annotations
~~~

Outside the container:

~~~bash
docker-compose run --rm php74-service php bin/console doctrine:database:create

docker exec -it mysql8-container bash
~~~

Inside the container

~~~bash
mysql -uroot -psecret

# Inside the mysql shell:
show databases;
# see the new database!
quit;
~~~

Add Encore via `composer req encore` to the PHP container.

Outside the container

~~~bash
docker-compose run --rm node-service yarn install
~~~
