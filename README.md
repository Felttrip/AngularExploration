# Exploration 1: AngularJS

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
