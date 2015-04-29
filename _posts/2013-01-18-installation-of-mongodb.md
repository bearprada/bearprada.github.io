---
layout: post
title: Installation of MongoDB
date: 2013-01-18 15:27:31
share: y
disqus: y
---

Introduction
============

MongoDB (from "humongous") is a scalable, high-performance, open source, document-oriented database. Written in C++.


Installation
============

- download it in here (depend on your platform)
- unzip it into a folder. example : c:\mongodb\
- create the database file path. example : c:\mongodb\data\
- execute the mongodb. c:\mongodb\bin\mongod --dbpath=c:\mongodb\data\
- the mongodb will open at port 27017(data connection) and 28017(control panel)
- open the browser and enter the URL( http://localhost:28017 , and see the result as follow :

Extension - Master and Slave Structure
======================================

Concept(working)
----------------

we setting the Master/Slave structure in local computer.

- create the database file paths : c:\mongod\master_data\, c:\mongod\slave_data1\, c:\mongod\slave_data2\
- start the master : c:\mongodb\bin\mongod --master --dbpath=c:\mongod\master_data\ --port 10000
- start the slave1 : c:\mongodb\bin\mongod --slave --source localhost:10000 --dbpath=c:\mongod\slave_data1\ --- port 20000
- start the slave2 : c:\mongodb\bin\mongod --slave --source localhost:10000 --dbpath=c:\mongod\slave_data2\ --- port 30000
- done

MongoDB on Grails
=================

Installation
------------

- grails create-app mongodbTest
- grails install-plugin mongodb-morphia
- add data source

```
grails-app/conf/DataSource.groovy

mongodb {
  host = 'localhost'
  port = 27017
  databaseName = 'test'
  username = "YOUR_USERNAME"
  password = "YOUR_PASSWORD"
}
```

- grails create-mongodb-class Car
- add some attributes for db-class

```
grails-app/mongo/Car.groovy

class Car{
    String brand
    String title
}
```

- grails generate-all Car
- grails run-app (make sure the mongodb is open)
- add some data by browser
- done

Future Work
===========

* Sharding structure(working)

Reference
=========

* [quick start mongodb](http://www.mongodb.org/display/DOCS/Quickstart+Windows)
* [Master Slave on mongodb](http://docs.mongodb.org/manual/core/master-slave/)
* [Mongodb Plugin on Grails](http://www.grails.org/plugin/mongodb-morphia)
* [Sharding Introduction](http://docs.mongodb.org/manual/core/sharding/)

