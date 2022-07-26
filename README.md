# Bean Scope

## Learning Goals

- Define bean scope.
- Give an overview of the various bean scopes.

## Introduction

The Spring container manages object instances (beans) which are automatically
injected into various fields and parameters. We can define the scope of these
beans, i.e., we can define when a bean is created, injected, and deleted. The
default scope of a bean is **singleton.**

## Different Bean Scopes

There are six bean scopes provided by Spring:

1. Singleton.
2. Prototype.
3. Request.
4. Session.
5. Application.
6. WebSocket.

The first two scopes (singleton and prototype) can be used in any Spring
application but the next four are only available in web applications.

### Singleton

This scope ensures that there is only a single bean created from each method. We
don’t have to explicitly set a bean’s scope to singleton because it is the
default. But we could do that using the `@Scope` annotation:

```java
@Bean
@Scope("singleton")
public Dog dog() { ... }
```

### Prototype

The prototype scope returns a new bean every time it has to be injected
somewhere. We can define it like so:

```java
@Bean
@Scope("prototype")
public Dog dog() { ... }
```

### Request

This scope creates beans that are available for the entire lifecycle of an HTTP
request. The request can be processed by several different components but they
will all use the same bean.

### Session

The beans created with this scope are available for the entire HTTP session that
may have multiple HTTP requests with the same cookies or session IDs.

### Application

This enables a broader scope than the singleton scope which is scoped to a
single application. The application scope makes the beans available for all
applications running in the same `ServletContext`.

### WebSocket

This enables beans to be created and available during a full WebSocket session
cycle.

## Conclusion

We have looked at how to define bean behavior by changing their scope. The
singleton scope is the default but for web applications we will use the request
and session scopes pretty often.

## Reference

- [Bean Scopes Docs](https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-factory-scopes)
