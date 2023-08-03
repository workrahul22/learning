#### Introduction

Under the hood, Nest makes use of robust HHTP Server framework like Express(the default) and optionally can be configured to use Fastify as well!

Nest provides a level of abstraction above these common Node.js frameworks (Express/Fastify), but also expose their APIs directly to the developer. This gives developers the freedom to use the myraid of third party modules which are available for the underlying platform.

#### Installation

To get started, you can either scaffold the project with the Nest CLI, or clone a starter project (both will produce the same outcome).

```bash
    $ npm i -g @nestjs/cli
    $ nest new project-name
```

Note: To create a new Typescript project with stricter feature set, pass the --strict flag to the nest new command



