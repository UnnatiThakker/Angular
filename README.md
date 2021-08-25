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

## Dynamic components

## Angular Elements

# Templates

- [ ] Task #1 [@Name](https://help.nuclino.com/988f802d-mention-a-team-member) 
- [ ] Task #2 [@Name](https://help.nuclino.com/988f802d-mention-a-team-member) 
- [ ] Task #3 [@Name](https://help.nuclino.com/988f802d-mention-a-team-member) 

# Directives

Classes to add additional behavior to elements.

## Types of Directives

1. Components - template based
2. Attribute Directives - changes appearance or behavior of element, component, or another directive. Ex: NgClass, NgStyle, NgModel
3. Structural Directives - changes DOM layouts by adding or removing DOM elements. Ex: NgIf, NgFor, NgSwitch

# Dependency Injection
	
# Refrences

* [Angular](https://angular.io/guide)
* ...
* ...
