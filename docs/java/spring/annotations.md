# :clipboard: ANNOTATIONS

## :pushpin: Spring Core

* `org.springframework.beans.factory.annotation.Autowired` - marks a constructor, field, setter method, or config method as to be autowired by Spring's dependency injection facilities

## :pushpin: Spring Boot

* `org.springframework.boot.autoconfigure.SpringBootApplication` - indicates a configuration class that declares one or more Bean methods and also triggers auto-configuration and component scanning

## :pushpin: Spring Web

* `org.springframework.stereotype.Component` - indicates that the class is a spring component
* `org.springframework.stereotype.Controller` - indicates that the class is a controller
  * `org.springframework.web.bind.annotation.RequestMapping` - maps web requests onto methods in request-handling classes with flexible method signatures
  * `org.springframework.web.bind.annotation.GetMapping`, `org.springframework.web.bind.annotation.PostMapping`, etc. - equivalent to `@RequestMapping(method = RequestMethod.GET)`, `@RequestMapping(method = RequestMethod.POST)`, etc.
* `org.springframework.web.bind.annotation.RestController` - equivalent to `@Controller` and `@ResponseBody` (indicates a method return value should be bound to the web response body)
  * `org.springframework.web.bind.annotation.PathVariable` - indicates a method parameter should be bound to a URI template variable
  * `org.springframework.web.bind.annotation.RequestBody` - indicates a method parameter should be bound to the body of the web request
* `org.springframework.web.bind.annotation.ControllerAdvice` - specialization of `@Component` for classes that declare `@ExceptionHandler`, `@InitBinder` or `@ModelAttribute` methods to be shared across multiple `@Controller` classes
* `org.springframework.stereotype.Service` - indicates that the class is a service
* `org.springframework.stereotype.Repository` - indicates that the class is a repository
* `org.springframework.context.annotation.Primary` - indicates that a bean should be given preference when multiple candidates are qualified to autowire a single-valued dependency
* `org.springframework.beans.factory.annotation.Qualifier` - indicates which implementation should be taken when autowiring. Just provide bean name (first letter in lower case) as a value
* `org.springframework.context.annotation.Profile` - if you have two beans named the same, you can switch between them using this annotation (only bean marked with active Profile will be in Application Context)
  * `@Profile({"EN", "default"})` - you can assign more profiles and also set **default** profile (used when there are no active profiles)
* `org.springframework.web.bind.annotation.ExceptionHandler` - allows handling exceptions in specific handler classes and/or handler methods
* `org.springframework.web.bind.annotation.ResponseStatus` - marks a method or exception class with the HTTP status code and reason that should be returned

## :pushpin: Spring Data JPA

* `jakarta.persistence.Entity` - indicates that the class is an entity which will be persisted to the database
* `jakarta.persistence.Id` - indicates the primary key of an entity
* `jakarta.persistence.GeneratedValue` - indicates the generation strategy for primary key. See `jakarta.persistence.GenerationType` enum for generation strategies
  * `@GeneratedValue(strategy = GenerationType.AUTO)` - indicates that primary key generation will be handled by database
* `jakarta.persistence.ManyToMany` - indicates a many-valued association with many-to-many multiplicity
  * `@JoinTable(name="author_book", joinColumns = @JoinColumn(name="book_id"), inverseJoinColumns = @JoinColumn(name = "author_id"))` - TODO

## :pushpin: Spring Test

* `org.springframework.boot.test.context.SpringBootTest` - annotation that can be specified on a test class that runs Spring Boot based tests. It provides **Spring Test Context**
* `org.springframework.test.context.ActiveProfiles` - indicates which active bean definition profiles should be used when loading an Application Context for test classes
