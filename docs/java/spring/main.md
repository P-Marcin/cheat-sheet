# :clipboard: SPRING FRAMEWORK

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
* [Thymeleaf](thymeleaf.md)

## :pushpin: Spring MVC

:star: **MVC** :star: stands for **Model View Controller** and it is a common design pattern for **GUI** and **Web Applications**.

Controller **handles requests**. It is responsible for **invoking business logic** and **populating Model**.

Model is a **POJO** **(Plain Old Java Object)** class which means that it **is not tied to any Java framework**.

View **handles rendering of the response** which contains Model **to HTML page**.

In Spring MVC there is :star: **Dispatcher Servlet** :star: which:
* receives request from Client
* passes the request to Controller and receives Model from Controller
* passes the Model to View and receives rendered HTML page
* passes rendered HTML page to Client

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

## :pushpin: HTTP

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
