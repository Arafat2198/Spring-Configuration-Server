![](https://forthebadge.com/images/badges/made-with-java.svg)
![](https://forthebadge.com/images/badges/kinda-sfw.svg)

# Spring-Configuration-Repository
Spring Cloud Config provides server-side and client-side support for externalized configuration in a distributed system. With the Config Server, you have a central place to manage external properties for applications across all environments. 
As an application moves through the deployment pipeline from dev to test and into production, you can manage the configuration between those environments and be certain that applications have everything they need to run when they migrate.
The default implementation of the server storage backend uses git, so it easily supports labelled versions of configuration environments as well as being accessible to a wide range of tooling for managing the content.

Note: You would be requiring Eclipse IDE for Java EE Developer for running Multiple Instances of the Limits Service, and Postman for making Blank POST Requests
### Make Sure you have the following Installed 
```bash
1) GIT
2) JAVA 8 or above
3) Erlang OTP 20.0 above
4) RabbitMQ
5) Postman - (for making Blank POST Requests)
6) Eclipse IDE for Java EE Developer - for running Multiple Instances of the Limits Service)
```

## Quick Start

### Creating the Limits REST Service using Spring Boot  
Go to start.spring.io create a Spring Boot project with the following Dependencies: 
```bash
1) spring-boot-starter-actuator
2) spring-boot-starter-web
3) spring-cloud-starter-config
4) spring-boot-devtools
5) spring-boot-starter-test
```
### Add Details of the Config Server
```bash
spring.config.import=optional:configserver:http://localhost:8888
```
### Setup the Spring cloud config server
Go to start.spring.io create a Spring Boot project with the following Dependencies: 
```bash
1) Spring Boot DevTools 
2) Config Server
```
Note: Since port 8080 is already in use by our application, we will use port 8888 for our config server
### Reload configuration from server (at runtime)

Spring Cloud Config has a `@RefreshScope` mechanism to allow beans to be reinitialized
on demand to fetch updated configuration values. The AppController on the client
has this annotation, so it will display the new config value once the refresh
endpoint is called.

Note: keep the server running in backround. The client app in the next step needs to connect to it.

### All the Important URI

```bash
GET http://localhost:8888/limits
```
This displays the config properties which are being retrieved from the git repo by the Config Server 

```bash
GET http://localhost:8080/limits
```
This displays the config properties which are being retrieved from the Config Server by the Git Repo for the Development env

```bash
GET http://localhost:8080/limits
```
This displays the config properties which are being retrieved from the Config Server by the Git Repo for the QA env

```bash
GET http://localhost:8080/limits/default
```
This displays the config properties which are being retrieved from the Config Server by the Git Repo for the Default env

```bash
GET http://localhost:8080/actuator
```
This displays all the Actuator EndPoints for a particular Microservice

```bash
POST http://localhost:8080/actuator/refresh
```
To refresh a single Microservices with the updated end points, send a Blank POST requests for this end point using POST Man
Note: This needs to be done for every Microservice

```bash
POST http://localhost:8080/actuator/refresh
```
To refresh all the Microservices with the updated end points, send a Blank POST requests for this end point using POST Man to any single Microserrvice 
Note: This needs to be done for every Microservice

