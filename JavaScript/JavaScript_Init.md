#JavaScript - Initalizing Your JavaScript Application#

Note: For a fantastic reference on terminal commands to start your first apps, please refer to [RyanShim24's CheatSheet](https://github.com/msyinmei/CheatSheet/blob/master/README.md). Much of this below is a repeat.

##Introduction##

###Node.js###

[Node.js](http://nodejs.org/) is a platform built on Chrome's JavaScript runtime for building fast, scalable network applications. Node.js uses an event-driven, non-blocking I/O (input/output) model great for data-intensive real-time applications that run across distributed devices.

How to start a Node.js app via the command line:

```shell
~ $ mkdir appName
~ $ touch app.js
~ $ touch .gitignore
~ $ git init
```

Add node_modules to your .gitignore folder (so that it doesn't get downloaded)

```shell
~ $ echo "node_modules" >> .gitignore

```

Initialize with node package manager and install & save dependencies

```shell
~ $ npm init
~ $ npm install --save express ejs pg lodash sequelize sequelize-cli bcrypt
```

Create database and initialize sequelize

```
~ $ createdb appName
~ $ sqlize init

```

Configurate your development, test and production files by changing to:

```js
{
  "development": {
    "database": "firstproject",
    "host": "127.0.0.1",
    "dialect": "postgres"
  },
  "test": {
    "database": "database_test",
    "host": "127.0.0.1",
    "dialect": "postgres"
  },
  "production": {
    "use_env_variable": "DATABASE_URL"
  }
}

```

For Authentication Only: Modify your route.js file:

```js

var routeMiddleware = {
  checkAuthentication: function(req, res, next) {
    if (!req.user) {
      res.render('login', {message: "Please log in first"});
    }
    else {
     return next();
    }
  },

  preventLoginSignup: function(req, res, next) {
    if (req.user) {
      res.redirect('/home');
    }
    else {
     return next();
    }
  }
};
module.exports = routeMiddleware;
```

Sample app.js file:

```js
//Require all dependencies
var express = require('express'),
    app = express(),
    bodyParser = require('body-parser'),
    methodOverride = require('method-override'),
    db = require("./models/index"),
    passport = require("passport"),
    request = require("request"),
    passportLocal = require("passport-local"),
    cookieParser = require("cookie-parser"),
    session = require("cookie-session"),
    flash = require("connect-flash");
    var routeMiddleware = require("./config/routes");

//For ejs, method-override and bodyparser
app.set('view engine', 'ejs');
app.use(express.static(__dirname + '/public'));
app.use(bodyParser.urlencoded({extended: true}));
app.use(methodOverride('_method'));

//Your routes and CRUD methods should go here
app.get('/', function(req, res){
  res.send('Hello World');
});

//Set up server to listen for PORT or localhost:3000
var server = app.listen(process.env.PORT || 3000, function() {
    console.log('Listening on port %d', server.address().port);
});

```



