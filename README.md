# api documentation for  [express.io (v1.1.13)](http://express-io.org)  [![npm package](https://img.shields.io/npm/v/npmdoc-express.io.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-express.io) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-express.io.svg)](https://travis-ci.org/npmdoc/node-npmdoc-express.io)
#### Realtime-web framework for nodejs

[![NPM](https://nodei.co/npm/express.io.png?downloads=true)](https://www.npmjs.com/package/express.io)

[![apidoc](https://npmdoc.github.io/node-npmdoc-express.io/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-express.io_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-express.io/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-express.io/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-express.io/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Brad Carleton",
        "email": "brad@techpines.com"
    },
    "bugs": {
        "url": "https://github.com/techpines/express.io/issues"
    },
    "contributors": [
        {
            "name": "Brad Carleton",
            "email": "brad@techpines.com",
            "url": "http://techpines.com"
        },
        {
            "name": "James Wyse",
            "email": "james@jameswyse.net",
            "url": "http://www.jameswyse.net"
        },
        {
            "name": "Edward Smith",
            "email": "ed@camayak.com",
            "url": "https://github.com/edwardmsmith"
        },
        {
            "name": "Krzysztof",
            "email": "pharcosyle@gmail.com",
            "url": "https://github.com/pharcosyle"
        }
    ],
    "dependencies": {
        "async": "0.1.22",
        "coffee-script": "1.4.0",
        "express": "~3.4.0",
        "socket.io": "~0.9.16",
        "underscore": "1.4.3"
    },
    "description": "Realtime-web framework for nodejs",
    "devDependencies": {
        "chai": "*",
        "jade": "*",
        "mocha": "*",
        "request": "*",
        "socket.io-client": "*"
    },
    "directories": {},
    "dist": {
        "shasum": "cfd60a2454bd33337d8ccd98ed97c3e7bcfe5d1f",
        "tarball": "https://registry.npmjs.org/express.io/-/express.io-1.1.13.tgz"
    },
    "homepage": "http://express-io.org",
    "keywords": [
        "realtime",
        "web",
        "framework",
        "express.io",
        "express",
        "socket.io",
        "badass"
    ],
    "main": "switch.js",
    "maintainers": [
        {
            "name": "brad@techpines.com",
            "email": "brad@techpines.com"
        }
    ],
    "name": "express.io",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/techpines/express.io.git"
    },
    "scripts": {
        "compile": "./node_modules/coffee-script/bin/coffee -o compiled/ -c lib/",
        "postpublish": "rm -rf $(cat /tmp/.pwd)/compiled",
        "prepublish": "echo $(pwd) > /tmp/.pwd; ./node_modules/coffee-script/bin/coffee -o compiled/ -c lib/;",
        "test": "./node_modules/mocha/bin/mocha test/test.coffee"
    },
    "version": "1.1.13"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module express.io](#apidoc.module.express.io)
1.  object <span class="apidocSignatureSpan">express.io.</span>io.middleware
1.  object <span class="apidocSignatureSpan">express.io.</span>io.request
1.  object <span class="apidocSignatureSpan">express.io.</span>io.room

#### [module express.io.middleware](#apidoc.module.express.io.middleware)
1.  [function <span class="apidocSignatureSpan">express.io.middleware.</span>routeForward (options)](#apidoc.element.express.io.middleware.routeForward)

#### [module express.io.request](#apidoc.module.express.io.request)
1.  [function <span class="apidocSignatureSpan">express.io.request.</span>RequestIO (socket, request, io)](#apidoc.element.express.io.request.RequestIO)

#### [module express.io.room](#apidoc.module.express.io.room)
1.  [function <span class="apidocSignatureSpan">express.io.room.</span>RoomIO (name, socket)](#apidoc.element.express.io.room.RoomIO)



# <a name="apidoc.module.express.io"></a>[module express.io](#apidoc.module.express.io)



# <a name="apidoc.module.express.io.middleware"></a>[module express.io.middleware](#apidoc.module.express.io.middleware)

#### <a name="apidoc.element.express.io.middleware.routeForward"></a>[function <span class="apidocSignatureSpan">express.io.middleware.</span>routeForward (options)](#apidoc.element.express.io.middleware.routeForward)
- description and source-code
```javascript
routeForward = function (options) {
  if (!_.isObject(options.config)) {
    options.type = options.config;
    options.config = configs[options.type];
    if (options.config == null) {
      throw new Error("RouteForwardError: No config for " + options.type);
    }
  }
  return function(request, response, next) {
    var index, match, meta, route, variable, _ref, _ref1, _ref2, _ref3;
    _ref = options.config;
    for (route in _ref) {
      meta = _ref[route];
      if (meta.method === request.method.toLowerCase()) {
        match = meta.regex.exec(request.url);
        if (match != null) {
          if ((_ref1 = meta.variables) == null) {
            meta.variables = [];
          }
          if ((_ref2 = request.params) == null) {
            request.params = {};
          }
          _ref3 = meta.variables;
          for (index in _ref3) {
            variable = _ref3[index];
            request.params[variable] = match[2 + parseInt(index)];
          }
          return request.io.route("" + match[1] + ":" + route);
        }
      }
    }
    return next();
  };
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.express.io.request"></a>[module express.io.request](#apidoc.module.express.io.request)

#### <a name="apidoc.element.express.io.request.RequestIO"></a>[function <span class="apidocSignatureSpan">express.io.request.</span>RequestIO (socket, request, io)](#apidoc.element.express.io.request.RequestIO)
- description and source-code
```javascript
function RequestIO(socket, request, io) {
  this.socket = socket;
  this.request = request;
  this.manager = io;
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.express.io.room"></a>[module express.io.room](#apidoc.module.express.io.room)

#### <a name="apidoc.element.express.io.room.RoomIO"></a>[function <span class="apidocSignatureSpan">express.io.room.</span>RoomIO (name, socket)](#apidoc.element.express.io.room.RoomIO)
- description and source-code
```javascript
function RoomIO(name, socket) {
  this.name = name;
  this.socket = socket;
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
