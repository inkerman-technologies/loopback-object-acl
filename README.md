# loopback-object-acl
Loopback provides great "class-level" ACL's for restricting access to a whole Model or its mehods, but greatly lacks the ability to restric access to individual objects. This project tries to solve this, by setting object-level ACL's on each object, and manipulates Loopback's Query to only return objects the requesting user has access to.

## Install

```
npm install --save loopback-object-acl
```

In `model-config.json` add `../node_modules/loopback-object-acl` to mixins

```js
  "_meta": {
    "sources": [
      "loopback/common/models",
      "loopback/server/models",
      "../common/models",
      "./models"
    ],
    "mixins": [
      "loopback/common/mixins",
      "loopback/server/mixins",
      "../common/mixins",
      "./mixins",
      "../node_modules/loopback-object-acl"
    ]
  }
```

### CurrentUser in context
This mixins expects a `currentUser` object on the `options` object. This is **not** default Loopback v3.x behavior, and must be implemented before usage.

Implementation can found here: http://loopback.io//doc/en/lb3/Using-current-context.html#use-a-custom-strong-remoting-phase

## Compatibility
This mixin is only tested with **Loopback v3.X** and using **MongoDB** as DataSource

## TODO

### Read-permissions
- [x] Do only return objects from database that the requesting user has access to.

### Write-permissions
Version 2.0

### Client
- [ ] Set ACL on object-creation
- [ ] Set permissions on user creation


### Tests
- [ ] ObjectAcl.js
- [ ] CurrentUserUtil.js

## License
```
MIT License

Copyright (c) 2017 Jesper Bruun Hansen

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```