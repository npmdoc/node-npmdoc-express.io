# npmdoc-express.io

#### api documentation for  [express.io (v1.1.13)](http://express-io.org)  [![npm package](https://img.shields.io/npm/v/npmdoc-express.io.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-express.io) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-express.io.svg)](https://travis-ci.org/npmdoc/node-npmdoc-express.io)

#### Realtime-web framework for nodejs

[![NPM](https://nodei.co/npm/express.io.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/express.io)

- [https://npmdoc.github.io/node-npmdoc-express.io/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-express.io/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-express.io/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-express.io/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-express.io/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-express.io/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Brad Carleton"
    },
    "bugs": {
        "url": "https://github.com/techpines/express.io/issues"
    },
    "contributors": [
        {
            "name": "Brad Carleton",
            "url": "http://techpines.com"
        },
        {
            "name": "James Wyse",
            "url": "http://www.jameswyse.net"
        },
        {
            "name": "Edward Smith",
            "url": "https://github.com/edwardmsmith"
        },
        {
            "name": "Krzysztof",
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
            "name": "brad@techpines.com"
        }
    ],
    "name": "express.io",
    "optionalDependencies": {},
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



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
