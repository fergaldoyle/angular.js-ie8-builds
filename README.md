AngularJS 1.3 / 1.4 IE8 builds
========================
AngularJS 1.3 / 1.4 does not work with IE8. With these custom builds you get good IE8 support. I can't guarantee that everything will work but anything I've tried works fine.

### What you need

* [es5-shim](https://github.com/es-shims/es5-shim)
* [jQuery 1.*](http://jquery.com/download/)
* AngularJS 1.4.* build from this repo (some poly-fills are baked in and minor fixes to enable IE8 support)

### Example
```html
<!DOCTYPE html>
<html>
<head>
	<meta http-equiv="X-UA-Compatible" content="IE=edge" />
	<meta charset="utf-8" />
	<title>Angular 1.4 IE8</title>
	<!--[if IE 8]>
		<script src="//cdnjs.cloudflare.com/ajax/libs/es5-shim/4.0.5/es5-shim.min.js"></script>
		<script src="//code.jquery.com/jquery-1.11.1.min.js"></script>
		<style>
			.ng-hide {
				display: none !important;
			}
		</style>
	<![endif]-->
	<script src="angular.js"></script>
</head>
<body ng-app="someApp">

</body>
</html>
```

### npm & bower

##### npm

	npm install angularjs-ie8-build
	
##### bower

	bower install angularjs-ie8-build
	
	// bower install with local name "angular"
	bower install angular=angularjs-ie8-build

### Careful now
When using `$q` promise methods `catch` or `finally` in IE8 use bracket notation instead of dot notation. Same goes for `$http` `delete` method. IE8 does not like dot notation with these reserved words.
```javascript
// no
promise.catch(function(){});

// yes
promise['catch'](function(){});
```

#### Other stuff
*   Use attributes for directives, e.g. `<div ng-view>` instead of custom element `<ng-view>`
*   If you want to use custom elements, you need to make IE8 aware of them first, e.g. `document.createElement('ng-view');`
*   Use `ng-style` instead of `style="{{ someCss }}"`
*   Check any additional angular or third party modules you are using for reserved words described above. If you find any, use a search and replace to change from dot notation to bracket notation



### Source
The source is maintained here:  
https://github.com/fergaldoyle/angular.js/tree/ie8-compat   
https://github.com/fergaldoyle/angular.js/tree/ie8-compat-1.4


