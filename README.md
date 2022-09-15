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

## Locally
 
Software       |  Version  |  Download
----------------|-----------|-----------------------------------------------
`NodeJS`       | `14.16.0` | https://nodejs.org/en/download/releases/  
`MYSQL`        | `8.0.27`  | https://dev.mysql.com/downloads/mysql/ 
`MongoDB`      | `4.4.4`   | https://www.mongodb.com/try/download/community 
`Apache Kafka` | `4.4.4`   | https://www.mongodb.com/try/download/community 

## Docker

Software         |  Version   |  Download
-----------------|------------|-----------------------------------------------
`Docker`         | `20.10.16` | https://www.docker.com/  
`Docker Compose` | `1.29.2`   | https://www.docker.com/ 

`Note: docker compose it will automatically be installed with docker, please install the latest version of docker.`
    
# Setup & Installation

* Locally
    - run kafka and zookeeper by default zookeeper running on port and kafka running on port 9092 if kafka is running on diffrent port
    you should configure its port on each service 
    if zookeper running on diffrent port you should edit server.propties and configure zookeper port  
    - run mysql on port 3306 
    if you are running mysql in diffrent porn you should configure database port envirement variable of user service
    - run mongodb
    running on port 27017
    if mongodb running on diffrent port you should configure database env variable of restaurant service
    - run services

    
    
    
    
    
    
* Docker
