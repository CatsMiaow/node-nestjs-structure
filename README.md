# node-nestjs-structure
Node.js framework NestJS project structure

### Installation
```sh
# 1. node_modules
$ npm i
# 2. edit env config
$ vim ./config/*.json
# 3. database model entity generate
$ npm run entity dbname
# OR
$ npm run entity dbname skip
$ npm run build:entity
```
If you use multiple databases, [modify them.](bin/entity.js#L31)

### Development
```sh
$ npm run start:dev
```
Run [http://localhost:3000](http://localhost:3000)

### Production
```sh
# define NODE_ENV yourself
$ npm run build
# OR
$ npm start
```

### Folders
```js
+-- bin // Custom tasks
+-- config // Env config files for `config` module
+-- dist // Source build
+-- public // Static Files
+-- src
|   +-- common // Nest Module, global
|   |   +-- controllers // Nest Controllers
|   |   +-- decorators // Nest Decorators
|   |   +-- dto // DTO (Data Transfer Object) Schema, Validation
|   |   +-- filters // Nest Filters
|   |   +-- guards // Nest Guards
|   |   +-- interceptors // Nest Interceptors
|   |   +-- interfaces // TypeScript Interfaces
|   |   +-- middleware // Nest Middleware
|   |   +-- pipes // Nest Pipes
|   |   +-- providers // Nest Providers
|   |   +-- * // models, repositories, services...
|   +-- entity // TypeORM Entities generated by `typeorm-model-generator` module
|   +-- * // Other Nest Modules, non-global, same as common structure above
+-- test // Jest testing
+-- typings // Modules or global type definitions
```

### Implements
* See [app](src/app.ts), [app.module](src/app.module.ts)
  - Database
  - Module Router
  - Static Files
  - Validation
* [Global Authenticated Guard](src/common/guards/authenticated.guard.ts)
* [Global Exception Filter](src/common/filters/exceptions.filter.ts)
* [Global Logging Middleware](src/common/middleware/logger.middleware.ts)
* [Session Login with Passport](src/base/providers/local.strategy.ts)
* [Custom Logger for Production](src/common/providers/custom-logger.service.ts)
* [AWS SDK Example](src/aws)
* Controller Routes
  - [Login](src/base/controllers/login.controller.ts)
  - [Sample](src/sample/controllers/sample.controller.ts) Parameter, [DTO](src/sample/dto/sample.dto.ts)
* [Database Query](src/sample/providers/database.service.ts) Sample


#### Links.
* [NestJS](https://docs.nestjs.com)
* [Nest Sample](https://github.com/nestjs/nest/tree/master/sample)
* [Awesome Nest](https://github.com/juliandavidmr/awesome-nestjs)
