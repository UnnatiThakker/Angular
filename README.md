# Angular
> **A design framework and development framework to create efficient and sophisticated SPA.**

## Angular Applications Essentials/Core Ideas

* Components
* Templates
* Directives

# Components

> Basic building blocks
>
> Controls View
>
> can be declared using @component decorator. It consist of metadata which tells Angular from where to get basic building blocks to create a view. 

It consists of:

* selector
* HTML template
* styles
* provides
* A typescript class to define it's behaviour 

Two ways to create:

* Angular CLI - `ng generate component <component_name>`
* Manual

Manual Creation:

* Create component file <component-name>.component.ts
* Write `import {component} from '@angular/core'` in the component file
*  Add @component decorator with its metadata

```
@component{
	selector: '<selector-name>',
	templateUrl: '<template-file-path>',
	styleUrls: [<style-file-path>],
    providers: [<list-of-providers>]
}
```

or

```
@component{
	selector: '<selector-name>',
	template: '<HTML-template>',
	styles: [<css>],
    providers: [<list-of-providers>]
}
```

* Create a class to include code for that component

```
export class ComponentClassName{
..............
}
```

## Component Lifecycles

* ngOnChanges()
* ngOnInit()
* ngDoCheck()
* ngAfterContentInit()
* ngAfterContentChecked()
* ngAfterViewInit()
* ngAfterViewChecked()
* ngOnDestroy()

## Component Interaction/Sharing data

* @Input decorator to pass input from parent to child
* @Output decorator to emit event from child to parent
* local variable (ex: #timer) to give reference of child component to access its properties and methods
* @ViewChild to get child reference
  * You can't use the *local variable* technique if the parent component's *class* relies on the child component's *class*. The parent-child relationship of the components is not established within each component's respective *class* with the *local variable* technique. Since the *class* instances are not connected to one another, the parent *class* cannot access the child *class* properties and methods.

    When the parent component *class* requires that kind of access, ***inject*** the child component into the parent as a *ViewChild*.
* Services

## Content Projection

 *project* content from the parent Component to the child Component using `<ng-content>`.

The downside is parent component does not have access to the child component's properties and methods.

**Three Types:**

1. Single-slot content projection
2. Multi-slot content projection
3. Conditional content projection 
	
# Decorators

design Pattern used to seprate modification or decoration of a class without modifying the original source code.
#### Types of Decorators
- Class Decorators, @component, @NgModule
- Property Decorators, @Input, @Output
- Method Decorators, @HostListener
- Parameter Decorators, @Inject
	
A Decorator is a special kind of declaration that can be attached to a class declaration, method, accessor, property, or parameter. Decorators use the form @expression, where expression must evaluate to a function that will be called at runtime with information about the decorated declaration.	

# Directives

Classes to add additional behavior to elements.

## Types of Directives

1. Components - template based
2. Attribute Directives - changes appearance or behavior of element, component, or another directive. Ex: NgClass, NgStyle, NgModel
3. Structural Directives - changes DOM layouts by adding or removing DOM elements. Ex: NgIf, NgFor, NgSwitch
	
Angular Directive is basically a class with a @Directive decorator. A component is also a directive-with-a-template. A @Component decorator is actually a @Directive decorator extended with template-oriented features. Whenever Angular renders a directive, it changes the DOM according to the instructions given by the directive. The directive appears within an element tag similar to attributes.	

# Interceptor

unique type of Angular Service that allow us to intercept incoming or outgoing HTTP requests using the HttpClient (i.e. modify or change the value of the request).

To use the same instance of HttpInterceptors for the entire app, import the HttpClientModule only in your AppModule, and add the interceptors to the root application injector . If you import HttpClientModule multiple times across different modules (for example, in lazy loading modules), each import creates a new copy of the HttpClientModule, which overwrites the interceptors provided in the root module.
	
# Services

singleton object
used to share data between classes
sepration of concern - write api calls, business logic, etc.
	
# Pipes

simple functions to transform data
can be used any where in application by declaring only once
	
# Interpolation

incorporate dynamic string values into your HTML templates
use double curly {{}} braces 
With interpolation, Angular performs the following tasks:
- Evaluates all expressions in double curly braces.
- Converts the expression results to strings.
- Links the results to any adjacent literal strings.
- Assigns the composite to an element or directive property.
	
# Binding

deals with how to bind data from component to template
it automatically keeps page upto date.

Types:
- Property
- Event
- Two-way
- Attribute
- Class
- Style

[For More Details on Each Type](https://angular.io/guide/binding-syntax#binding-types-and-targets)
	
# Template Reference Variable

-> reference to a DOM element within a template
-> it can also be a reference to an Angular component or directive or a web component
-> use # symbol to create
Usually, the reference variable can only be accessed inside the template. However, you can use ViewChild decorator to reference it inside your component.

Working with <ng-template>
We use the prefix let- to declare the input variable fullName
this variable fullName is visible inside the ng-template, not the outside
In order to access the variable inside ng-template, we have the declare the context	
	
# Dependency Injection
	
design pattern in angular which has its own implementation

It allows us to inject dependencies in different components across our applications, without needing to know, how those dependencies are created, or what dependencies they need themselves.

Types:
- Model Injector
can be configured inside Ngmodel and injectable annotations
- Element Injector
which is beed created for every element and can be configuered inside component or directive annotation there's a providers property, define inside this array. 

[For More Details on DI](https://blog.thoughtram.io/angular/2015/05/18/dependency-injection-in-angular-2.html)	
	
### How Angular results these dependencies?

When component declare some dependency, angular first of all tries to resolve it in its own element injector, means element injector of this component which declare this dependency. And if there is no provider for it, angular asks a parent element injector and it goes up, up, and up, until it finds it. If it can't find, it goes back to the same place where its started and tries to resolve it in model injector.If it doesn't find there then will give error 'No Provider found'. Otherwise runs the code.

### Resolution Modifiers
1. @Optional()
If it can't resolved at runtime, Angular simply resolves the service as null without error.
2. @Self()
Angular will look at the element injector for the current component of directive.
3. @Skipself()
Opposite to @self(). It will skip Element Injector for the current component and will start looking from a parent.
4. @host()
designate a component as the last stop in the injector tree when searching for providers.	
	
# Refrences

* [Angular](https://angular.io/guide)
* ...
* ...
