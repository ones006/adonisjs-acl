# AdonisJS ACL
![npm](https://img.shields.io/npm/dt/@ones006/adonisjs-acl?style=plastic)
![npm (scoped)](https://img.shields.io/npm/v/@ones006/adonisjs-acl)
![NPM](https://img.shields.io/npm/l/@ones006/adonisjs-acl)

Version [for **Adonis v6**]

This package allows you easily add role/permission based access to your [AdonisJS](https://adonisjs.com/) applications routes:

## Available Features
- Role based route authentication
- Permission based route authentication

## Requirements
- Adonisjs v6
- Node >=8
- Mysql >=5
- PostgreSQL >=10


## Dependencies
- Adonisjs5 [lucid(`@adonisjs/lucid`)](https://docs.adonisjs.com/guides/database/introduction)
- Adonisjs5 [auth(`@adonisjs/auth`)](https://docs.adonisjs.com/guides/auth/introduction)

## Installation

You can install the package via NPM:
``` bash
npm install @ones006/adonisjs-acl
```
Or with yarn
``` bash
yarn add @ones006/adonisjs-acl
```

## Setup
- Configure package with `node ace configure @ones006/adonisjs-acl`
- In `start/kernel.ts`, add the following to `Server.middleware.registerNamed`:
```
is: () => import('App/Middleware/Is'),
can: () => import('App/Middleware/Can'),
```
- Update `config/rolePermission.ts` to customize table names
- Run migration to create role and permission tables: `node ace migration:run`
## Usage
### Role Based Access
```
Route.get('/something-important', 'ImportantController.show').middleware('is:administrator')
```
#### Multiple Roles
```
Route.get('/something-important', 'ImportantController.show').middleware('is:administrator,superadmin')
```
### Permission Based Access
```
Route.get('/important', 'SomeController.show').middleware('can:view-important')
```
#### Multiple Roles
```
Route.get('/important', 'SomeController.show').middleware('can:view-important,read-important')
```
><span style="color:red">NB: User is granted access if they have one or more role/permission specified</span>

## Todo
- Add properties to models e.g `User.hasRole`, `User.hasPermission`, `role.hasPermission`, etc

## Contributing
If you have a feature you'd like to add, kindly send a Pull Request (PR)

## Security
If you discover any security related issues, please email [ones006@gmail.com](mailto:ones006@gmail.com) instead of using the issue tracker.

## Credits
- [Ones006](https://github.com/ones006)
- [All Contributors](../../contributors)

## License
The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
