#JavaScript - Initalizing Your JavaScript Application#

Note: For a fantastic reference on terminal commands to start your first apps, please refer to [RyanShim24's CheatSheet](https://github.com/msyinmei/CheatSheet/blob/master/README.md). Much of this below is a repeat.

##Introduction##

###Node.js Setup###

[Node.js](http://nodejs.org/) is a platform built on Chrome's JavaScript runtime for building fast, scalable network applications. Node.js allows your to write JavaScript code that can run on your computer free of any web browser. Node.js uses an event-driven, non-blocking I/O (input/output) model great for data-intensive real-time applications that run across distributed devices.

You can also install Node-based tools tools using the NPM (Node Package Manager) to install them. [Grunt](http://gruntjs.com/) is a popular Node-based tool used to automate common tasks like compiling Sass files to CSS, making JavaScript files smaller so they load in less time and compressing images to smaller file sizes. [Bower](http://bower.io/) is a package manager for the web that manages all your web files: javascript, css and images.

You can install Node JS and NPM on a Mac using [Homebrew](http://brew.sh/):

```shell
~ $ brew install node
```

In order to update and upgrade:

```shell
~ $ brew update
~ $ brew upgrade node
```

You can also uninstall using Homebrew:

```shell
~ $ brew uninstall node
```


####How to start a Node.js app via the command line####

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

```shell
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

####Creating Models for Database####
Using sequelize with express.js, we can create models using postgresQL on the back-end

Here's the official documentation on sequelizejs.com:
http://sequelizejs.com/articles/express

Here's how to create a User model:

Terminal Command:

```shell
~ $ sqlize model:create --name User --attributes username:string, password:string'
```

Your user migration:

```js
"use strict";
module.exports = {
  up: function(migration, DataTypes, done) {
    migration.createTable("Users", {
      id: {
        allowNull: false,
        autoIncrement: true,
        primaryKey: true,
        type: DataTypes.INTEGER
      },
      username: {
        type: DataTypes.STRING,
        unique: true,
        allowNull: false
      },
      password: {
        type: DataTypes.STRING
      },
      createdAt: {
        allowNull: false,
        type: DataTypes.DATE
      },
      updatedAt: {
        allowNull: false,
        type: DataTypes.DATE
      }
    }).done(done);
  },
  down: function(migration, DataTypes, done) {
    migration.dropTable("Users").done(done);
  }
};

```

Your user model:

```js
"use strict";

var bcrypt = require("bcrypt");
var passport = require("passport");
var passportLocal = require("passport-local");
var salt = bcrypt.genSaltSync(10);

module.exports = function (sequelize, DataTypes){
   var User = sequelize.define('User', {
     username: {
        type: DataTypes.STRING,
        unique: true,
        allowNull: false,
        validate: {
          len: [6, 30]
        }
    },
    password: DataTypes.STRING
    },

  {
    classMethods: {
      associate: function(models) {
        User.hasMany(models.Food,{onDelete: "NO ACTION"});
    },
      encryptPass: function(password) {
        var hash = bcrypt.hashSync(password, salt);
        return hash;
    },
      comparePass: function(userpass, dbpass) {
      // don't salt twice when you compare....watch out for this
        return bcrypt.compareSync(userpass, dbpass);
    },
      createNewUser:function(username, password, err, success ) {
        if(password.length < 6) {
          err({message: "Password should be more than six characters"});
        }
        else{
        User.create({
            username: username,
            password: this.encryptPass(password)
          }).done(function(error,user) {
            if(error) {
              console.log(error)
              if(error.name === 'SequelizeValidationError'){
              err({message: 'Your username should be at least 6 characters long', username: username});
            }
              else if(error.name === 'SequelizeUniqueConstraintError') {
              err({message: 'An account with that username already exists', username: username});
              }
            }
            else{
              success({message: 'Account created, please log in now'});
            }
          });
        }
      },
      } // close classMethods
    } //close classMethods outer

  ); // close define user

  passport.use(new passportLocal.Strategy({
      usernameField: 'username',
      passwordField: 'password',
      passReqToCallback : true
    },

    function(req, username, password, done) {
      // find a user in the DB
      User.find({
          where: {
            username: username
          }
        })
        // when that's done,
        .done(function(error,user){
          if(error){
            console.log(error);
            return done (error, req.flash('loginMessage', 'Oops! Something went wrong.'));
          }
          if (user === null){
            return done (null, false, req.flash('loginMessage', 'Username does not exist.'));
          }
          if ((User.comparePass(password, user.password)) !== true){
            return done (null, false, req.flash('loginMessage', 'Invalid Password'));
          }
          done(null, user);
        });
    }));

  return User;
}; // close User function

```





