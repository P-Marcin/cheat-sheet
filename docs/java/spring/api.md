# :clipboard: API

Legend:
* :green_circle: - class
* :orange_circle: - abstract class
* :white_circle: - interface

## :pushpin: Spring Core

* :white_circle: `org.springframework.context.ApplicationContext` - central interface to provide configuration for an application
    * You can use `getBean` method to get the bean instance that uniquely matches the given object type, if any

## :pushpin: Spring Boot

* :green_circle: `org.springframework.boot.SpringApplication` - class that can be used to bootstrap and launch a Spring application from a Java main method
* :white_circle: `org.springframework.boot.CommandLineRunner` - indicates that a bean should **run** every time that Spring Boot starts up

## :pushpin: Spring Web

* :white_circle: `org.springframework.ui.Model` - defines a holder for model attributes

## :pushpin: Spring Data JPA

* :white_circle: `org.springframework.data.repository.CrudRepository<T, ID>` - defines generic CRUD operations on a repository for a specific type
