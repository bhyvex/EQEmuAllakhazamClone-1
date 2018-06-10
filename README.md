# EQEmuAllakhazamClone

* This clone was originally created in 2004 by Muuss of our Emulator community, I've since gone through and cleaned quite a few things up but it still could use a complete rewrite as the internals are terrible to work with but this is an ancient PHP app and much has changed since
* If you are interested in using this for your server, it is plenty functional and below is the instructions to do so

![](https://i.imgur.com/pwTrZm2.png)

![](https://i.imgur.com/oMC9mDM.png)

### Setup

* Clone this repository into a webserver directory and then make a copy of the config file in `includes`

```cp includes/config.template.php includes/config.php```

* You will need to set your database variables and most importantly your site URL

### Developing Using Docker

* We have a docker environment ready to go, on Linux/Mac environments there are helper scripts that you can run
* We're using the following services in this docker stack
  * nginx
  * php-fpm 7.2
  * mariadb

### Starting the docker environment

```./docker-up.sh```

Or

```cd laradock && docker-compose up -d nginx mariadb workspace && cd ..```

### Stopping the docker environment

```./docker-down.sh```

Or

```cd laradock && docker-compose down && cd ..```

### Development Database 

* If you already have a database to point to, you can simply use whatever database server you'd like in your config and you 
can simply start the nginx container via `docker-compose up -d nginx workspace` while you are in the `laradock` folder

* Assuming you are using the laradock setup mentioned above, you will need to source in a database, we've provided a handy
script to do just that

```docker-compose exec workspace php seed-db.php```