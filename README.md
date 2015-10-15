# angular.i18n.properties
lightweight angular module for providing internationalization to angular from ‘.properties’ files

it's a simple rewrite of https://github.com/jquery-i18n-properties/jquery-i18n-properties in angular style without use of JQuery

## Usage

### Using the module
1. Include it on your ``<head>`` section after your angular.js files:

```html
<script type="text/javascript" language="JavaScript"
  src="js/angular.i18n.properties.min.js"></script>
```

2. Initialize the module, and access a translated value (assuming a key named ‘some.key‘ exists in the properties.Messages_en exists):

```html
<script>
	var app = angular.module("myApp", ['angularI18nProperties']);
	
	app.controller('myCtrl', ['i18nProperties', function(i18nProperties) {
	  var mctrl = this;
	
	  // you better deport this into a service if you have more than one controller
    mctrl.changeLang(lang) {    
      i18nProperties.i18n.properties({
        name : 'Messages',
        language : lang,
        path : 'properties/',
        mode : 'map',
        cache : false,
        callback : function() {
          //some action you want after trad is complete
        }
      });
    };
    
    mctrl.changeLang('en'); // init by default to english
	}]);
	
</script>
```

then in your html page
```html
<div ng-controller="myCtrl as mctrl" ng-cloak>
  <h3 class="panel-title">{{'my.title' | translate}}</h3>
  <button type="button" class='btn btn-default' ng-click="mctrl.changeLang('fr')">{{'french' | translate}}</button>
  <button type="button" class='btn btn-default' ng-click="mctrl.changeLang('en')">{{'english' | translate}}</button>
</div>
```

### Building a minified JavaScript file

1. Install the closure compiler tool:

   ``apt-get update && apt-get install closure-compiler``

2. Run it:

   ``closure-compiler --js angular.i18n.properties.js \
                    --js_output_file angular.i18n.properties.min.js``
