# costume-party

## 1. SQL Commands for creating database + user
we create a db for every project and aa specific user in the db for that project. This is for security purposes 
```
create database costume_party;
create user 'batman'@'localhost' identified by 'yellowpencil';
grant all privileges on costume_party.* to 'batman'@'localhost';

```

##2. Environment Variables
Our environment variables are stored in .env but may be declared if needed 
```
DB_USER=batman
DB_PWD=yellowpencil
DB_NAME=costume_party
DB_TYPE=mysql
DB_SERVER=localhost
```

## 3. Database Connect

a database connection is defiend inside of db.js. It contains all code to be connected to mySQL

```js
//./models/db.js
'use strict';

//loads environment variables from .env
require('dotenv').config();


//knex is a database adapter for ndoe
//npm install knex && npm install lodash
//lodash is a dependency of knex
var db = require('knex')({
	client: process.env.DB_TYPE,
	connection: {
		host: process.env.DB_SERVER,
		user: process.env.DB_USER,
		password: process.env.DB_PWD,
		database: process.env.DB_NAME
	}
});



module.exports = db;

```