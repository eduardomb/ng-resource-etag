# ng-resource-etag

This is a fork of [AngularJS 1.5.3 ng-resource module](https://github.com/angular/angular.js/blob/v1.5.3/src/ngResource/resource.js) to support **eTag** on **If-Match** header.

## Install
```shell
bower install ng-resource-etag
```

## Usage
A new argument `ifMatch` can be passed to each resource action. This argument
should contain the name of the key that holds the **eTag** on the resource
instance.

```javascript
var User = $resource('/user/:userId', {userId:'@id'}, {
    update: {'method': 'PATCH', ifMatch: '_etag'}
});

User.get({userId:123}, function(u) {
  console.log(u._etag);  // This must return the _etag
  u.abc = true;  // Change the original user
  u.$update();
});
```

## Full Documentation
Full documentation is available on the
[AngularJS docs site](http://docs.angularjs.org/api/ngResource).
