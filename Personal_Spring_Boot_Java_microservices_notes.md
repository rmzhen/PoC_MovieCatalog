# Personal Spring Boot Java microservices notes

## Spring Boot annotations
```java
@RestController
```
This annotation tells SpringBoot that the current class is a RestController.

```java
@RequestMapping("/url")
``` 
```java
@RequestMapping("/{var}")
```
This annotation tells SpringBoot to load up the current class with the URL in the brackets. The curly brachets '{}' means the URL is based on the defined variable.

```java
@Bean
```
This annotation tells SpringBoot to make a singleton out of the instance it's attached to.

```java
@Autowired
```
This annotation tells SpringBoot to inject a Bean of the same type to the given instance.

## main/resources/application.properties
This is the config file of the Spring application where you can specify what the application needs to do on startup.

```
server.port="portnumber"
```
This tells the Spring Boot to use the specified port instead of the default port. (Default: 8080)

## Making REST calls from code
### RestTemplate class
```java
RestTemplate.getForObject(url, object);
```
This makes a call to the given URL and converts the received json string into the specified object. 
*Note: RestTemplate will become deprecated sometime in the future. Use WebClient as alternative.*

```java
WebClient.Builder foobar = WebClient.builder();
```
This creates a WebClient instance you can use for making REST calls using WebClient.
[List of WebClient functions](https://docs.spring.io/spring-framework/docs/5.1.0.RELEASE_to_5.1.1.RELEASE/Spring%20Framework%205.1.1.RELEASE/org/springframework/web/reactive/function/client/WebClient.html)

## Eureka server
```
eureka.client.register-with-eureka=false
eureka.client.fetch-registry=false
```
These lines need to be placed in the "application.properties" file to let the Eureka server know not to register the server as a client. This is because a Eureka server is also a Eureka client.