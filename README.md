# Exploration 1: AngularJS
Exploration Results can be found at cs4830.cloudapp.net/AE

The tutorial I chose to follow was the one provided at [angularjs.org](https://docs.angularjs.org/tutorial/).
I chose to use this tutorial because it touched on several parts of AngularJS
that are fundemental to understanding how the framework works.

Particular components that were explored were
* [Angular Templates](https://docs.angularjs.org/guide/templates)
* [Filtering Repeaters](https://docs.angularjs.org/guide/filter)
* [Two-way Data Binding](https://docs.angularjs.org/guide/databinding)
* [XHRs & Dependency Injection](https://docs.angularjs.org/guide/di)
* [Templating Links & Images](https://docs.angularjs.org/guide/templates)
* [Routing With Multiple Views](https://docs.angularjs.org/tutorial/step_07)
* [Custom Filters](https://docs.angularjs.org/guide/filter)
* [Event Handlers](https://docs.angularjs.org/tutorial/step_10)
* [REST and Custom Services](https://docs.angularjs.org/guide/services)
* [Applying Animations](https://docs.angularjs.org/guide/animations)

Over all working with AngularJS was really interesting. Its one of my first in depth
experiences with a true front-end framework.

## Templating

As expected angular has view templating
baked in.  AngularJS markup is wrapped in curly-braces `{{like-so}}` which is identical
to handlebars. I suspect that that would cause a lot of issues if you wanted to use
handlebars as your templating engine instead of the built in one. AngularJS uses
what they call directives to enable powerful manipulation of the DOM. directives
are attributed added to html tags that are prepended with `ng-` allowing AngularJS
to find them and determine the action to be taken. A couple of simple directives
that I used were `ng-repeat` and `ng-src`.

## Filtering

Filtering is a really powerful tool in AngularJS. Take this simple list of phones.
(You can see the useage of `ng-repeat` and useage of `{{ }}`)
```
<ul class="phones">
  <li ng-repeat="phone in phones"
      class="thumbnail phone-listing">
    <a href="#/phones/{{phone.id}}" class="thumb"><img ng-src="{{phone.imageUrl}}"></a>
    <a href="#/phones/{{phone.id}}">{{phone.name}}</a>
    <p>{{phone.snippet}}</p>
  </li>
</ul>
```

You can add a filter to this list really easily by adding an input to the page with
an `ng-model` directive  and adding the filter criteria to the `ng-repeat` directive
like so
(You can see the useage of `ng-repeat` and useage of `{{ }}`)
```
<input ng-model="query">`
<ul class="phones">
  <li ng-repeat="phone in phones | filter: query"
      class="thumbnail phone-listing">
    <a href="#/phones/{{phone.id}}" class="thumb"><img ng-src="{{phone.imageUrl}}"></a>
    <a href="#/phones/{{phone.id}}">{{phone.name}}</a>
    <p>{{phone.snippet}}</p>
  </li>
</ul>
```
Those two small changes will create a page that will auto filter the items in the list
without any further code.

## Two-way Data Binding

The core to Angulars magic is it's two-way data binding. Without going into specifics,
AngularJS will keep all of a variable in sync across the entire application.  This is
what makes the previous example work. When the `<input>` tag is updated, the `ng-model`
called `query` is also updated with the contents of the `<input>`.  When `query` has been
update this applies across the entire page causing the `filter` property to now have a
string to filter against.  This is then applied to the `ng-repeat` directive causing the
items that are shown to be filtered by the given filter.

## Routing

Having a router in the front end of an application is really interesting and I like it a lot.
By allowing the front end of the application to handle the routes this gives the developer
the freedom to build the server side of the application purely as a data feed.  This is
especially useful if there are plans to make an api for the application because it will
already exist! The syntax for writing a router is super simple and encourages an MVC
centric architecture.
```
$routeProvider.
  when('/phones', {
    templateUrl: 'partials/phone-list.html',
    controller: 'PhoneListCtrl'
  }).
  when('/phones/:phoneId', {
    templateUrl: 'partials/phone-detail.html',
    controller: 'PhoneDetailCtrl'
  }).
  otherwise({
    redirectTo: '/phones'
  });
  ```

## Other Features
AngularJS has tons of additional features. A few of the ones I used were Event Handlers,
Custom Services and Animations.  These features add additional functionality and enable
writing clean readable code, which can be a daunting task for the front end.
