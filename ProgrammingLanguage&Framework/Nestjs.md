#### Introduction

Under the hood, Nest makes use of robust HHTP Server framework like Express(the default) and optionally can be configured to use Fastify as well!

Nest provides a level of abstraction above these common Node.js frameworks (Express/Fastify), but also expose their APIs directly to the developer. This gives developers the freedom to use the myraid of third party modules which are available for the underlying platform.

#### Installation

To get started, you can either scaffold the project with the Nest CLI, or clone a starter project (both will produce the same outcome).

```bash
    $ npm i -g @nestjs/cli
    $ nest new project-name
```

#### Controller

Controller are responsible for handling incoming requests and returning response to the client.

The response status code is always 200 by default, except for POST requests which use 201. we can easily change this behaviour by adding the @HttpCode decorator

### Interceptors

An interceptors is a class annotated with @Injectable decorator and implements the NestInterceptor interface. They make it possible to 

1. bind extra logic before/after method execution.
2. Transform the result returned from a function.
3. Transform the exception thrown from a function.
4. Extend the basic function behaviour.
5. Completly override a function depending on specific conditions (e.g for caching purpose)






