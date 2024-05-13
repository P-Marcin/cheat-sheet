# :clipboard: SPRING FRAMEWORK

<p>
  <a href="https://spring.io/projects/spring-framework#learn" rel="noreferrer">
      <img src="https://img.shields.io/badge/Documentation-2088E9?logo=quickLook&logoColor=white" alt="Documentation"/>
  </a>
</p>

## :pushpin: Overview
:star: **Spring Framework** :star: is the most popular Java framework for building **highly scalable** and **reliable** Enterprise Applications.
It is well suited for **Monolithic** and **Microservice Architecture**.

Spring Framework was introduced by :star: **Rod Johnson** :star: in **2003** as a **simpler alternative to J2EE.** In **March 2004** version **1.0** has been released.

## :pushpin: Spring Framework vs Spring Boot
Spring Framework is a **collection of framework libraries**.

:star: **Spring Boot** :star: is **automated tooling** for Spring Framework applications. Think of it as a **wrapper** around Spring.
One of the best feature of Spring Boot is **auto-configuration** of application based on the jar dependencies.

## :pushpin: Spring Initializr
Quickly **generate** Spring Boot project: **[start.spring.io](https://start.spring.io)**

## :pushpin: Cheat Sheets

* [Annotations](annotations.md)
* [API](api.md)
* [Properties](properties.md)
* [Project Lombok](project-lombok.md)
* [Thymeleaf](thymeleaf.md)
* [Mockito](mock-mvc.md)
* [JsonPath](json-path.md)

## :pushpin: SOLID principles of Object-Oriented Programming

* :star: **Single Responsibility** :star: - every class should have a single responsibility. Classes should be small
* :star: **Open Closed** :star: - classes should be open for extension, but closed for modification
* :star: **Liskov Substitution** :star: - objects in a program would be replaceable with instances of their subtypes without altering the correctness of the program. A square **is** a rectangle, a rectangle **is not** a square.
* :star: **Interface Segregation** :star: - make fine-grained interfaces that are client specific. Notice relationship to the Single Responsibility principle
* :star: **Dependency Inversion** :star: - abstractions should not depend upon details and details shold depend upon abstractions. Important that higher level and lower level objects depend on the same abstract interaction

:exclamation: A key theme is **avoiding tight coupling** in your code. At the same time **be pragmatic** when following SOLID: every request path **does not need its own Controller class**.

## :pushpin: Dependency Injection

:star: **Dependency Injection** :star: is where a **needed dependency is injected by another object**.

Types of Dependency Injection:
* :star: **By class fields (using `@Autowired` on a field)** :star: - least preferred
  * Can be `public` or `private` properties. Using `private` properties is evil as spring can use reflection to set them. It "works", but is slow and makes testing difficult.
* :star: **By setters (using `@Autowired` on a setter)** :star: - for **optional** dependencies
* :star: **By constructor** :star: - for **mandatory** dependencies, **most preferred**

Dependency Injection can be done with **concrete Classes** **(should be avoided)** or with **Interfaces** **(preferred)**.

:exclamation: **Best Practice:** declare property `private final` and initialize in the constructor.

## :pushpin: Inversion of Control (IoC)

:star: **Inversion of Control** :star: is a technique to allow dependencies to be injected at runtime. Control of the dependencies **is being inverted over to managing framework**.

## :pushpin: Spring Bean Lifecycle

Start:
1. Instantiation of Bean
2. Population of properties/dependencies
3. Call `setBeanName` of `org.springframework.beans.factory.BeanNameAware`
4. Call `setBeanFactory` of `org.springframework.beans.factory.BeanFactoryAware`
5. Call `setApplicationContext` of `org.springframework.context.ApplicationContextAware`
6. Pre Initialization (call `postProcessBeforeInitialization` of `org.springframework.beans.factory.config.BeanPostProcessor`)
7. Call `@PostConstruct` annotated method
8. Call `afterPropertiesSet` of `org.springframework.beans.factory.InitializingBean`
9. Call custom `init` method (can be set with `initMethod` of `org.springframework.context.annotation.Bean`)
10. Post Initialization (call `postProcessAfterInitialization` of `org.springframework.beans.factory.config.BeanPostProcessor`)
11. Bean ready to use

Termination:
1. Container shutdown
2. Call `@PreDestroy` annotated method
3. Call `destroy` of `org.springframework.beans.factory.DisposableBean`
4. Call custom `destroy` method (can be set with `destroyMethod` of `org.springframework.context.annotation.Bean`)
5. Bean terminated

:exclamation: There are over **14** `Aware` interfaces which are used to **access the Spring Framework infrastructure**.

## :pushpin: HTTP (Hypertext Transfer Protocol)

### :bell: Versions

* **HTTP/1.1** - added more **caching strategies** and **request methods** (`PUT`, `PATCH`, `DELETE`, `CONNECT`, `TRACE` and `OPTIONS`). Since this version **HTTP connection can be reused (Keep-Alive)**.
* **HTTP/2** - improves **the average speed of communications** by **lowering latency** and **higher throughput**. No significant changes for Developers
* **HTTP/3** - most important change is use of the **QUIC + UDP** transport protocols instead of TCP. This slightly improves **the average speed of communications**. No significant changes for Developers

### :bell: Request Methods

* :green_square: :blue_square: :orange_square: `GET` - requests for a resource (e.g. HTML file)
* :green_square: :blue_square: :orange_square: `HEAD` - is like GET, but only requests for meta information without the body
* :orange_square: `POST` - requests to post data to the server (e.g. form data). It is **create** request
* :blue_square: `PUT` - requests to create a new resource or replace a representation of the target resource with the state defined by the representation enclosed in the request. It is **create or replace** request
* :orange_square: `PATCH` - requests to apply a modification to a target resource according to the partial update defined in the representation enclosed in the request. It is **update** request
* :blue_square: `DELETE` - requests to delete the specified resource
* `CONNECT` - requests to establish a TCP/IP tunnel to the origin server identified by the request target. It is used to secure two-way communication through one or more HTTP proxies with SSL/TLS
* :green_square: :blue_square: `OPTIONS` - returns the HTTP methods supported by the server for the specified URL
* :green_square: :blue_square: `TRACE` - echo the received request. Can be used to see if request was altered by intermediate servers

Legend:
* :green_square: - Safe Methods: do not cause any changes on the server
* :blue_square: - Idempotent Methods: multiple identical requests will have the same effect on the server
* :orange_square: - Cacheable Methods: response is allowed to be stored for future use (cached)

### :bell: Response Status Codes

Full list: https://developer.mozilla.org/en-US/docs/Web/HTTP/Status
* **1xx** - informational
* **2xx** - successful
* **3xx** - redirection
* **4xx** - client error
* **5xx** - server side error

## :pushpin: REST (Representational State Transfer)

**Representation** - typically **JSON** or **XML**

**State Transfer** - typically via **HTTP**

## :pushpin: Marshalling vs Unmarshalling

:star: **Marshalling** :star: - process of converting Java Objects to JSON or XML

:star: **Unmarshalling** :star: - process of converting JSON or XML to Java Objects

## :pushpin: RMM (Richardson Maturity Model)

RMM is used to describe the quality of the RESTful service:
* **Level 0: Swamp of POX (Plain Old XML)** - uses **one URI** and **one kind of HTTP Verb** (Request Method)
  * Example: RPC, SOAP, XML-RPC
* **Level 1: Resources** - uses **multiple URIs** to identify specific resources and **one kind of HTTP Verb**. It breaks large service into **distinct URIs**.
  * Example: You can GET `/product/1234` and `/product/5678`
* **Level 2: HTTP Verbs** - uses **multiple URIs** and **multiple kind of HTTP Verb** for desired actions. It introduces HTTP Verbs to implement actions.
  * Example: You can GET and DELETE `/product/1234` and `/product/5678`
* **Level 3: Hypermedia** - representation **contains URIs** which may be useful to consumers. It helps developers **explore the resource**. It provides **discoverability**, making the API more **self documenting**
  * Spring Framework provides an implementation of :star: **HATEOAS (Hypermedia as the Engine of Application State)** :star: - in response objects you get links and information about the actions

## :pushpin: RESTful Best Practices

* After **201** (Created) status response return `Location` HTTP Header with URI to the new resource
* Do not return stack trace to client - be careful to not "leak" information to Internet

## :pushpin: Spring Boot DEV Tools

Spring Boot DEV Tools are **additional set of tools** that can make the application development experience **a little more pleasant**:
* application **automatically restart** whenever files on the classpath change (in IntelliJ IDEA you can just `Recompile java file` or `Build Project` in `Build` top menu)
* starts embedded **LiveReload** server that can be used to **trigger a browser refresh** when a resource is changed
* **disable caching options** by default, so changes can be seen immediately
* you can configure **global DEV Tools settings** by adding a file named `.spring-boot-devtools.properties` to your `${HOME}` folder. Any properties added to this file will apply to **all** Spring Boot applications on your machine that use DEV Tools

## :pushpin: Spring MVC

Spring MVC is **blocking** (because uses Java Servlet API) and **non-reactive**.

:star: **MVC** :star: stands for **Model View Controller** and it is a common design pattern for **GUI** and **Web Applications**.

Controller **handles requests**. It is responsible for **invoking business logic** and **populating Model**.

Model is a **POJO** **(Plain Old Java Object)** class which means that it **is not tied to any Java framework**.

View **handles rendering of the response** which contains Model **to HTML page**.

In Spring MVC there is :star: **Dispatcher Servlet** :star: which:
* receives request from Client
* passes the request to Controller and receives Model from Controller
* passes the Model to View and receives rendered HTML page
* passes rendered HTML page to Client

### :bell: Spring RestTemplate

RestTemplate is in **maintenance mode** (no new features are planned). It is recommended to **use Spring WebClient for new development**.

## :pushpin: Spring WebFlux

Spring WebFlux is **non-blocking** (because does not use Java Servlet API) and **reactive**.

WebFlux uses project **Reactor** to provide reactive web services. It follows very closely to the configuration model of Spring MVC.

### :bell: Spring WebFlux.fn

Spring WebFlux.fn is a functional programming model used to define endpoints. It is alternative to annotation based configuration.

### :bell: Spring WebClient

Spring WebClient is **reactive** web client. By default, uses **Reactor Netty** - a **non-blocking** HTTP Client library.

## :pushpin: Testing

* Unit Tests - designed to test specific sections of code. Ideal coverage is **70-80%**.
* Integration Tests - designed to test behaviors between objects and parts of the overall system. They can include the Spring Context, database and message brokers.
* Functional Tests - testing the running application.

Spring MVC Controllers are tricky to test property. They have a high degree of integration with Spring MVC framework. JUnit tests are not sufficient to test the framework interaction.

Spring Mock MVC is a testing environment for the testing of Spring MVC Controllers:
* Provides mocks of the Servlet runtime environment (simulates the execution of controller as if it was running under Spring with Tomcat)
* Can be run with (Integration Test) or without (true Unit Test) Spring Context

Spring Boot supports a concept of :star: **Test Splices** :star: which bring up a targeted segment of the auto-configured Spring Boot environment:
* e.g. just the Database components or just the Web components
* user defined Spring beans typically are not initialized

:star: **@WebMvcTest** :star: is a Spring Boot test splice which creates a MockMVC enrionment for the controller under a test. Dependencies of it are not included and need to be added to the Spring Context in the test environment.

