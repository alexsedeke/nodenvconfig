# nodenvconf

**nodenvconf** primary extend the  [konphyg](https://github.com/pgte/konphyg) to read environment variables with predefined prefix 
and override the static konphyg values.

### What is konphyg?
**konphyg** is a smart lib reading cascading configuration files easy. You just define your folder containing your 
json configuration files. **konphyg** read them all and merge them to one object, separated by filename inside.
**konphyg** also use the NODE_ENV paramenter to read only environment specific configuration files. That way on 
NODE_ENV = 'dev' files named <name>.dev.json (database.dev.json) will be used and extend and override basic files like database.json.

### So why nodenvconf?
**nodenvconf** read and transform enviroment variables to objects and override the konphyg created objects. 
That way it's easy to maintain on Systems like heroku your app configuration dynamicly without the need of new deploy.
You can change api path, auth tokens and other things lightning fast.    
And even more. You can use ist also with your frontend application.

## Install
    $ npm install konphyg
    
## Usage
```js
// Initialize nodenvconf
var nodenvconf = require('nodenvconf');
// set nodenvconf options dispatch 
var config = nodenvconf({configDir: __dirname + '../config', pefix: 'nodenv', delimiter: '_'}).dispatch();
```

## Extend usage
**nodenvconf** can be also used without konphyg. Just let the configDir option parameter out. 
If nodenvconf is initialized without configDir option, konphyg will not be used.

## Options
The options is a object which accept following properties:
    
**prefix**    
Is a string defining the environment parameters to watch for, followed by delimiter! Default is 'nodenv'.
    
**delimiter**    
Is a string using as delimiter for object structure.    

**configDir**    
Is a path for konphyg to the configuration files.

**configDomain**    
Is a domain for konphyg to read only specified domain(filename) of the configuration files.