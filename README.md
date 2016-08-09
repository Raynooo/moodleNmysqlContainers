# moodleNmysqlContainers

TODO

##What it does

The *docker-compose.yml* config file in this project's root folder has the recipe to build two images called *moodle31* and *mysql57-for-moodle*.
- *moodle31* can create containers running **moodle 3.1** stable following jauer's recipe (see sources below).
- *mysql57-for-moodle* creates containers hosting a **mysql 5.7** server and automatically creating a database called moodle and its associated user with the appropriate rights granted.

*moodle31* containers will expose their 80 port and both images will have their containers sharing content-holding folders.


##How to run it

To build the images (if you have **docker-compose** installed and running), from inside its folder simply type :
```
docker-compose build moodle
```

###Changing shared directories

TODO

###Changing moodle server's address

TODO

## Sources

The dockerfiles used in this project are HEAVILY based on these two projects :

- jauer's [moodle repository](https://hub.docker.com/r/jauer/moodle/)
- MySQL's official [Server Docker Images](https://github.com/mysql/mysql-docker)

Both were modified to either use a specific version of a software or follow moodle's best practices.
