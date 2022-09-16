<div align="center">
  <a href="https://github.com/ITManZero/foodle">
    <img
      src="https://i.ibb.co/kSrvc6Q/restaurant.png"
      alt="Foodle Logo"
      height="64"
    />
  </a>
  <br />
  <p>
    <h3>
      <b>
        Foodle
      </b>
    </h3>
  </p>
  <p>
    <b>
      A Restaurant Management API
    </b>
  </p>
  <p>
 

  <p align="center">A <a href="https://docs.nestjs.com/v8/" target="blank">Nest.js 8</a> server built over microservice architecture with <a href="https://docs.nestjs.com/cli/monorepo" target="blank">monorepo</a> mode.</p>
    <p align="center">
  
<a href="http://nodejs.org/"><img src="https://img.shields.io/badge/node-^14.16.0-blue" alt="node" /></a>
<a href="http://nestjs.com/"><img src="https://img.shields.io/badge/framework-nestjs-red" alt="nestjs Framework" /></a>
<a href="" target="_blank"><img src="https://img.shields.io/badge/coverage-60%25-green" alt="Coverage" /></a>
<a href="http://nodejs.org/"><img src="https://img.shields.io/badge/docker-^20.10.16-yellow" alt="docker" /></a>

  </br>
  </br>
    <a href="https://hoppscotch.io/#gh-dark-mode-only" target="_blank">
      <img
        src="https://user-images.githubusercontent.com/73588285/190106491-5488a683-057b-46c7-8b95-d51e805c66f2.png"
        alt="architecture"
        width="100%"
      />
    </a>  
    </br>
    </br>
</div>

# Introduction
This server handle the complex business behind restaurants management operations.

Our system should be able to have multiple restaurants and branches, events like acctepting and rejecting customer orders, our server is responible to manage work of each reastaurant and its branches theire menus and meals.


# Services
- `Authentication Service:` tells wether a request is auhtenticated or not.
- `Restaurant Service:` responsible to manage restauarants, branches, menus and meals. 
- `User Service:` 
  - Tells wether the user is exisits or not.
  - Manages user types and roles.

# Folder Structer
```sh
+-- bin // Custom tasks
+-- dist // Source build
+-- public // Static Files
+-- lib/common // Global Nest Library
    +-- config // Environment Configuration
    +-- entities // TypeORM Entities or Mongoose Schemas
    +-- factories // dynamic objects building
    +-- enums // Constant value and Enum
    +-- controllers // Nest Controllers
    +-- decorators // Nest Decorators
    +-- dto // DTO (Data Transfer Object) Schema, Validation
    +-- filters // Nest Filters
    +-- guards // Nest Guards
    +-- interceptors // Nest Interceptors
    +-- interfaces // TypeScript Interfaces
    +-- middleware // Nest Middleware
    +-- pipes // Nest Pipes
    +-- providers // Nest Providers
    +-- modules // Nest Providers
    +-- services // Nest Services
    +-- utils // utility class
+-- apps // microservices
    +-- service-1
    +-- service-2
    +-- service-3
        +- test // Jest testing
        +-- src
            +-- module-1
            +-- module-2
            +-- module-3
                +-- config // Environment Configuration
                +-- entity // TypeORM Entities or Mongoose Schemas
                +-- constants // Constant value and Enum
                +-- controllers // Nest Controllers
                +-- services //Nest Services
                +-- dto // DTO (Data Transfer Object) Schema, Validation
                +-- decorators // Nest Decorators
                +-- filters // Nest Filters handle exceptions
                +-- guards // Nest Guards protect endpoint
                +-- interceptors // Nest Interceptors control the execution context
                +-- interfaces // TypeScript Interfaces
                +-- middleware // Nest Middleware
                +-- pipes // Nest Pipes
                +-- providers // Nest Providers
                +-- helpers // manipulates enums , casting types
                +-- module-3.module.ts
            +-- service-3.module.ts
            +-- main.ts
```
# Requirements

## Manual Build
 
Software       |    Version    |  Download
---------------|---------------|-----------------------------------------------
`NodeJS`       | `14.16.0`     | https://nodejs.org/en/download/releases/  
`MYSQL`        | `8.0.27`      | https://dev.mysql.com/downloads/mysql/ 
`MongoDB`      | `4.4.4`       | https://www.mongodb.com/try/download/community/
`Apache Kafka` | `2.0.0`       | https://mega.nz/file/g8IVXb7A#jKmDAbPItuny0K4J8KGWL91iqY6ISKBgZ2P2JIPi4Vw/
`Java`         | `11` or newer | https://www.oracle.com/java/technologies/downloads/archive/  

## Docker Build

Software         |  Version   |  Download
-----------------|------------|-----------------------------------------------
`Docker`         | `20.10.16` | https://www.docker.com/  
`Docker Compose` | `1.29.2`   | https://www.docker.com/ 

`Note: docker compose it will automatically be installed with docker, please install the latest version of docker.`
    
# Setup & Installation

##  **Running Manually** 

  1. **Configuration**
     * *zookeeper*: by default the server running on port `2181`, if the port is not avaliable in your machine you can configure the server from file called                  `zookeeper.properties` in the following dirictory `path-to-kafka/config/`.
     * *kafka:*  by default the server running on port `9092`, if the port is not avaliable in your machine you can configure the server from file called
       `server.properties` in the following dirictory `path-to-kafka/config/`.
     * *mysql:*  default port `3306`.
     * *mongodb:* defaut port `27017`.
     * *microservices:* 
     
       Each services has two build stages `development` and `production`, and each stage has has it's own env file. 
       
       All env files follow one [template](template.env), also we devided environment variables to groups and we call it  `Config NameSpaces`, to see all defined
       config namespaces you can find them [here](CONFIG-NAMESPACES..md).
       
       Now each seervice can choose what it need of configuration to load as following:
       
       - ***auth-service***
         ```sh
         const configNameSpaces = [
          ConfigNameSpace.APP,
          ConfigNameSpace.AUTH,
          ConfigNameSpace.MESSAGE_BROKER ];
         ConfigLoaderModule.forFeature( configNameSpaces , envFilePath);
         ```
       - ***user-service*** 
         ```sh
         const configNameSpaces = [
          ConfigNameSpace.APP,
          ConfigNameSpace.DATABASE,
          ConfigNameSpace.MESSAGE_BROKER ];
         ConfigLoaderModule.forFeature( configNameSpaces , envFilePath);
         ```
       - ***restaurant-service***
         ```sh
         const configNameSpaces = [
          ConfigNameSpace.APP,
          ConfigNameSpace.DATABASE,
          ConfigNameSpace.MESSAGE_BROKER ];
         ConfigLoaderModule.forFeature( configNameSpaces , envFilePath);
         ```
         You can configure a service from `.env` file which is for production stage or from `development.env` which is for development stage.
         
  2.  **Installing Dependencies**
      ```sh
      npm install
      ```
      
  4.  **Running Services**
 
      * start kafka and zookeeper server 
      
        
          ```sh
          # for windows
          cd path-to-kafka/bin/windows
          zookeeper-server-start.bat ../../config/zookeeper.properties
          kafka-server-start.bat ../../config/server.properties
         
          
          # for linux
       
          cd path-to-kafka/bin
          zookeeper-server-start.sh ../config/zookeeper.properties
          kafka-server-start.sh ../config/server.properties
          ```
      
      * start services
      
        **dev**
       
        
        ```sh
        # for windows
        npm run start:dev <service-name>
        # ex: 
        npm run start:dev auth-service

        # for linux
        npm run start-l:dev <service-name>
        # ex:
        npm run start-l:dev auth-service
        ```
        
        **debug**
        
        
        
        ```sh
        # for windows 
        npm run start:debug <service-name>
        # ex: 
        npm run start:debug auth-service
        
        # for linux
        npm run start-l:debug <service-name>
        # ex: 
        npm run start-l:debug auth-service
        ```
        
        **production**
        ```sh
        npm run build <service-name>
        node dist/apps/<service-name>/main
        # ex: 
        npm run build auth-service
        node dist/apps/auth-service/main
        ```
    
    
## **Running With Docker**

   1. **Download** `docker-compose` file
      ```sh
      curl https://cdn.filestackcontent.com/FGBF2ksrSNqfHFi5ylHD > docker-compose.yml
      ```
   2. **Configuration**
      
      You can edit `docker-compose.yaml` and add environment variable to each services.
      
      See [environment variables](#Environment-Variables).
      
      See [configuration namespaces](CONFIG-NAMESPACES..md).
      
      See [services Config namespaces](#Running-Manually).
      
   3. **Running Services**

      - Make sure that docker and docker-compose is running:
      
        ```sh
        docker -v
        docker-compose -v
        ```
        you should see smth like this 
        ```sh
        C:\kafka\bin\windows>docker -v
        Docker version 20.10.16, build aa7e414

        C:\kafka\bin\windows>docker-compose -v
        docker-compose version 1.29.2, build 5becea4c
        ```
      - Open directory where you dowwnloaded `docker-compos.yaml` file and run:
     
        ```sh
        docker-compose up -d
        ```
        
        to stop containers run:
        ```sh
        docker-compose down
        ```
   4. **Testing Endpoint**
    
      * auth-service is running on http://localhost:3005
      * user-service is running on http://localhost:3000
      * restaurant-service is running on http://localhost:3333
      
      See [API Docs]().
      

# Environment Variables

##### App configuration
|Name                   |Description
|-----------------------|-------------------------------
|`APP_NAME`  |Application or service name.
|`APP_ENVIRONMENT`     |Application or service environment.
|`DEBUG_ACTIVE`     |Turn on debug level.
|`SEED_ACTIVE`       |Seed the database always if set to true, default: `false`.
|`APP_SECRET`|Any secret key.



#### Auth configuration
|Name                   |Description
|-----------------------|-------------------------------
|`JWT_TOKEN_EXPIRATION`          |Expiration time of signed token.
|`JWT_SECRET `|Secret key to encode a token and decode it.


##### DataBase configuration
| Name                     |Description
|--------------------------|-------------------------------
| `DATABASE_DRIVER`               |Database driver (mysql, mongodb) works only for typeorm.
| `DATABASE_HOST`               |Host address.
| `DATABASE_PORT`                   |Database Server Port.
| `DATABASE_SCHEMA`  |Name of database.
| `DATABASE_ROOT_USERNAME`  |Root username.
| `DATABASE_ROOT_PASSWORD`    |Root password.
| `DATABASE_AUTO_LOAD`            | Auto match entities changes and updates with database.
| `DATABASE_SYNC`     | Auto match entities changes and updates with database

##### Message Broker configuration
| Name                     |Description
|--------------------------|-------------------------------
| `KAFKA_BROKERS`               |Kafka server host.
| `KAFKA_CONSUMER_GROUPE_ID`               |Unique groupe id.
| `KAFKA_CLIENT_ID`                   |Any client name.
| `SERVICE_TOKEN_NAME`  |InjectionToken.

# RoadMap

  - [x] #739 Auth Service
  
  - [x] Restaurnat Service
  
  - [x] User Service
  
  - [x] Success Response Formmatter
  
  - [x] Handling HttpException
  - [x] Config NameSpace Loader
  
  - [ ] Handling RpcException
  - [ ] Ordering Service
  
  - [ ] Payment Service

  - [ ] API Gateway
  - [ ] Load Balancing
  - [ ] Tesitng

# Contact Me
  - Email: baker.mesl.bm@gmail.com
  - linkedin: [Bakr Mslamni](https://www.linkedin.com/in/bakr-mslmani-263a7b218)
