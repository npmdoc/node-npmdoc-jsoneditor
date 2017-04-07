# api documentation for  [jsoneditor (v5.5.11)](https://github.com/josdejong/jsoneditor)  [![npm package](https://img.shields.io/npm/v/npmdoc-jsoneditor.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-jsoneditor) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-jsoneditor.svg)](https://travis-ci.org/npmdoc/node-npmdoc-jsoneditor)
#### A web-based tool to view, edit, format, and validate JSON

[![NPM](https://nodei.co/npm/jsoneditor.png?downloads=true)](https://www.npmjs.com/package/jsoneditor)

[![apidoc](https://npmdoc.github.io/node-npmdoc-jsoneditor/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-jsoneditor_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-jsoneditor/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-jsoneditor/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-jsoneditor/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Jos de Jong",
        "email": "wjosdejong@gmail.com"
    },
    "bugs": {
        "url": "https://github.com/josdejong/jsoneditor/issues"
    },
    "dependencies": {
        "ajv": "3.8.8",
        "brace": "0.8.0",
        "javascript-natural-sort": "0.7.1"
    },
    "description": "A web-based tool to view, edit, format, and validate JSON",
    "devDependencies": {
        "gulp": "3.9.1",
        "gulp-clean-css": "2.0.5",
        "gulp-concat-css": "2.2.0",
        "gulp-shell": "0.5.2",
        "gulp-util": "3.0.7",
        "json-loader": "0.5.4",
        "mkdirp": "0.5.1",
        "mocha": "2.4.5",
        "uglify-js": "2.6.2",
        "webpack": "1.12.14"
    },
    "directories": {},
    "dist": {
        "shasum": "1e06d4f09e42189ee63891e2435d091a9bd0017a",
        "tarball": "https://registry.npmjs.org/jsoneditor/-/jsoneditor-5.5.11.tgz"
    },
    "gitHead": "3117789ed7d7886b36b92c57b71264d43a0063b3",
    "homepage": "https://github.com/josdejong/jsoneditor",
    "license": "Apache-2.0",
    "main": "./index",
    "maintainers": [
        {
            "name": "josdejong",
            "email": "wjosdejong@gmail.com"
        }
    ],
    "name": "jsoneditor",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/josdejong/jsoneditor.git"
    },
    "scripts": {
        "build": "gulp",
        "test": "mocha test",
        "watch": "gulp watch"
    },
    "tags": [
        "json",
        "editor",
        "viewer",
        "formatter"
    ],
    "version": "5.5.11"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module jsoneditor](#apidoc.module.jsoneditor)
1.  [function <span class="apidocSignatureSpan">jsoneditor.</span>registerMode (mode)](#apidoc.element.jsoneditor.registerMode)
1.  object <span class="apidocSignatureSpan">jsoneditor.</span>modes



# <a name="apidoc.module.jsoneditor"></a>[module jsoneditor](#apidoc.module.jsoneditor)

#### <a name="apidoc.element.jsoneditor.registerMode"></a>[function <span class="apidocSignatureSpan">jsoneditor.</span>registerMode (mode)](#apidoc.element.jsoneditor.registerMode)
- description and source-code
```javascript
registerMode = function (mode) {
  var i, prop;

  if (util.isArray(mode)) {
    // multiple modes
    for (i = 0; i < mode.length; i++) {
      JSONEditor.registerMode(mode[i]);
    }
  }
  else {
    // validate the new mode
    if (!('mode' in mode)) throw new Error('Property "mode" missing');
    if (!('mixin' in mode)) throw new Error('Property "mixin" missing');
    if (!('data' in mode)) throw new Error('Property "data" missing');
    var name = mode.mode;
    if (name in JSONEditor.modes) {
      throw new Error('Mode "' + name + '" already registered');
    }

    // validate the mixin
    if (typeof mode.mixin.create !== 'function') {
      throw new Error('Required function "create" missing on mixin');
    }
    var reserved = ['setMode', 'registerMode', 'modes'];
    for (i = 0; i < reserved.length; i++) {
      prop = reserved[i];
      if (prop in mode.mixin) {
        throw new Error('Reserved property "' + prop + '" not allowed in mixin');
      }
    }

    JSONEditor.modes[name] = mode;
  }
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
