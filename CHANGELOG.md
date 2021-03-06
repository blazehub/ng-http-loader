# Changelog

## v2.2.0

This release adds the possibility to filter HTTP requests that should not be handled by the interceptor by providing an array of HTTP methods to the component's ``filteredMethods`` property.

## v2.1.0

This release introduces the **minimum duration** option. It gives the possibility to force a minimum duration during which the spinner should be visible.
You can mix this parameter with the **debounce delay** option:

```xml
<spinner 
    [debounceDelay]="100"
    [minDuration]="300">
</spinner>
```

```
Debounce delay: 100ms
Min. duration time: 300ms
---0ms--------100ms------------180ms-----------400ms--
----|----------|-----------------|---------------|---- 
req starts  spinner shows    req ends     spinner hides
```

``SpinnerVisibilityService#visibilityObservable`` and ``PendingInterceptorService#pendingRequestsStatus`` have been respectively deprecated in favor of ``visibilityObservable$`` and ``pendingRequestsStatus$`` (note the **$**).

## v2.0.0

The module bundling now uses [ng-packagr](https://github.com/dherges/ng-packagr).  
From now, you must use ``import { xxxxxxx } from 'ng-http-loader'`` without referencing the full path.

Also, ``NgHttpLoaderServicesModule`` && ``NgHttpLoaderComponentsModule`` have been removed and merged back to ``NgHttpLoaderModule``.  
The ``injectables`` now take advantage of the new [Tree Shakable Providers features](https://blog.angular.io/version-6-of-angular-now-available-cc56b0efa7a4).  
The integration in much cleaner, particularly with lazy loaded modules, and avoids the static ``forRoot()`` boilerplate. 

## v1.0.3

Some compiler options have been reverted, so the compilation target is ``es5`` like before v1.0.2.

## v1.0.2

The compiler options have been adjusted so ng-http-loader is now an es2015 module, and can be tree-shaked.

## v1.0.1

This release is a bug fix release. It prevents the ``PendingInterceptorService`` from being triggered when using the ``SpinnerVisibilityService``.  
See this [issue](https://github.com/mpalourdio/ng-http-loader/issues/64) for more details.

## v1.0.0

This release introduces full support for angular 6 & RxJS 6.

## v0.9.1

This release fixes a bug on the SpinKit Sk-Wave component that only appeared after template inlining.

See [this thread](https://github.com/tobiasahlin/SpinKit/issues/139) for details.

## v0.9.0

This release adds the more friendly SpinnerVisibilityService#show() && SpinnerVisibilityService#hide() methods as public API.  
The ``visibilitySubject`` introduced in v0.8.0 is now a ``ReplaySubject``, and its getter returns now an observable.

See the [Manually show and hide the spinner](https://github.com/mpalourdio/ng-http-loader#manually-show-and-hide-the-spinner) section.

## v0.8.0

This release adds the ``SpinnerVisibilityService``, a simple injectable service that allows you to manually show/hide the spinner.

See the [Manually show and hide the spinner](https://github.com/mpalourdio/ng-http-loader#manually-show-and-hide-the-spinner) section.

## v0.7.1

This release is a bug fix release. It slightly improves the behavior of the ``filteredUrlPatterns`` so this parameter takes care of query strings too.

## v0.7.0

This release adds the ``entryComponent`` property. It allows to specify your own component instead of the built-in ones. It uses the [NgComponentOutlet](https://angular.io/api/common/NgComponentOutlet) feature.

See the [Defining your own spinner](https://github.com/mpalourdio/ng-http-loader#defining-your-own-spinner) section.

## v0.6.0

This release adds the ``debounceDelay`` parameter (default is 0). It allows to discard the spinner for fast and repeated HTTP requests, which can be annoying under some conditions.

See [customization](https://github.com/mpalourdio/ng-http-loader#customizing-the-spinner)

The library footprint has been reduced by minifying templates and stylesheets before inlining them.

The library now takes advantage of [RxJS lettable operators](https://github.com/ReactiveX/rxjs/blob/master/doc/lettable-operators.md)

## v0.5.1

This release fixes a bug that could cause the spinner to not show if an HTTP request were performed **before** the spinner component was initialized.  
The responsible ``Subject`` has been replaced by a ``ReplaySubject``.

## v0.5.0

The module is now splitted in sub-modules for more convenience. See [usage](https://github.com/mpalourdio/ng-http-loader#usage).  
It's an **opt-in** feature. The "old" module import method, by simply declaring ``NgHttpLoaderModule``, is still fully supported. 

**BC break**: paths of components and services have changed.
- Components are now located in the ``components`` folders.
- Services are now located in the ``services`` folders.

## v0.4.0

Added **angular 5** full support. The last version compatible with angular 4 is ``version 0.3.4``

## v0.3.4

Fixed default spinners background.

## v0.3.0

This release gives the possibility to filter HTTP requests that should not be handled by the interceptor by providing an array of URL regex to the component's ``filteredUrlPatterns`` property.

## v0.2.0

Definitely switch to the new HttpClientModule api available from angular 4.3

## v0.1.0

Before completely removing HttpInterceptorService, provide a parallel implementation based on the new built-in angular 4.3 intercepto
