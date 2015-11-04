# webStorage
angular module for simply save data (single values, object, array) into browser local storage for web and mobile app.

## Add module on your angular app
```javascript
var app = angular.module('myAppName', ['webStorage']);
```

## Using prefix
You can use prefix that will be added before each variable name to distinguish same variable name between more apps.

```javascript
app.run(['$localStorage', function($localStorage){
  $localStorage.setPrefix('myAppName_');
}]);
```
Add prefix is similar to create a "namespace" for your app. If you set prefix, it will be added automatically in all future call to manage only local storage params with your namespace.

# Get & Set
## Single value
Inject service in controller and use it.

```javascript
app.run(['$localStorage', function($localStorage){

  $localStorage.set('key1', 'Hello');
  console.log($localStorage.get('key1'));

}]);
```

## JSON Object
```javascript
app.controller('ExampleCtrl', ['$localStorage', function($localStorage){

  // JSON Object
  $localStorage.set('key2', {title: 'Hello'});
  console.log($localStorage.get('key2'));
  
}
```

## Array 
```javascript
app.controller('ExampleCtrl', ['$localStorage', function($localStorage){

  // Array of Objects
  $localStorage.set('key3', [{title: 'Hello'}, {title: 'World'}]);
  console.log($localStorage.get('key3'));
  
}
```

## Remove
```javascript
app.controller('ExampleCtrl', ['$localStorage', function($localStorage){

  // Remove single key
  $localStorage.remove('key1');
  
  // Remove multiple keys at the same time
  $localStorage.remove(['key2', 'key3']);
  
  // Remove all keys in your "prefix namespace"
  //if you don't declare your personal "prefix" this call will delete all local storage
  $localStorage.clear();
}
```
