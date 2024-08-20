
**How does an Angular application work?**

An Angular application works by building a Single Page Application (SPA). It starts by loading an index.html file, which contains a root element. Angular takes control of the root element and dynamically updates the content based on user interactions and application logic. Angular uses components, services, directives, and modules to manage the application's structure and behavior. When a user interacts with the app, Angular's data binding updates the view automatically without reloading the entire page.

**What is TypeScript?**

TypeScript is a superset of JavaScript that adds static types and other features, such as classes, interfaces, and modules, to make code more robust and maintainable. Angular is built using TypeScript, allowing developers to write cleaner, more predictable code that is easier to debug.

**Write a pictorial diagram of Angular architecture.**

Unfortunately, I cannot create pictorial diagrams directly, but I can describe it. Angular architecture includes:

1. **Modules:** Organize the app into cohesive blocks of functionality.
2. **Components:** Define views and behaviors of the app.
3. **Templates:** HTML with Angular directives and binding syntax.
4. **Services:** Business logic and data handling.
5. **Dependency Injection:** Manages the lifecycle of services.
6. **Directives:** Custom behaviors added to elements in the DOM.
7. **Routing:** Handles navigation between views.

**What is metadata?**

Metadata in Angular is used to provide additional information about a class. It is added using decorators, such as `@Component`, `@NgModule`, etc. For example, the `@Component` decorator adds metadata to a class to define it as a component and provides details like the template, styles, and selector.

**What is the difference between constructor and ngOnInit?**

- **Constructor:** This is a default method that is called when a class is instantiated. It's used for dependency injection and initializing class members.
- **ngOnInit:** This is a lifecycle hook provided by Angular, which is called after the component's constructor and after Angular has initialized all the data-bound properties. It's typically used for additional initialization tasks that require the component to be fully set up.

**How is Dependency Hierarchy formed?**

In Angular, a dependency hierarchy is formed by injecting services into components, where services can be provided at different levels of the component tree. When a service is provided at a module level, it is available to all components in that module. When provided at a component level, it is only available to that component and its children, creating a hierarchical structure.

**What is the purpose of the async pipe?**

The `async` pipe in Angular is used to automatically subscribe to an observable or promise and get the latest emitted value. It also automatically unsubscribes when the component is destroyed, preventing memory leaks.

**What is the option to choose between inline and external templates?**

In Angular, templates can be defined either inline, within the `@Component` decorator using the `template` property, or in an external HTML file using the `templateUrl` property. Inline templates are suitable for simple and small views, while external templates are better for more complex layouts.

**What is the purpose of the ‘ngFor’ directive?**

The `ngFor` directive is used to loop through an array and repeat a block of HTML for each item in the array. It is commonly used for rendering lists in Angular.

**What is the purpose of the ngIf directive?**

The `ngIf` directive conditionally includes or excludes a block of HTML based on a Boolean expression. If the expression evaluates to true, the block is included; otherwise, it is removed from the DOM.

**What happens if you use the script tag inside the template?**

Using the `<script>` tag inside an Angular template is generally discouraged because Angular sanitizes the HTML to prevent XSS (Cross-Site Scripting) attacks. The `<script>` tag will be removed, and any JavaScript code inside it will not be executed.

**What are template statements?**

Template statements are expressions or methods that respond to user actions in Angular templates. They are usually bound to events like clicks or input changes and are defined using event binding syntax, such as `(click)="onClick()"`.

**How do you categorize data binding types?**

Data binding in Angular can be categorized into:
1. **Interpolation:** Binding data from the component to the template using `{{ }}`.
2. **Property Binding:** Binding component data to DOM properties using `[property]="value"`.
3. **Event Binding:** Binding DOM events to component methods using `(event)="method()"`.
4. **Two-way Binding:** Combining property and event binding to keep the data in sync using `[(ngModel)]`.

**What is a parameterized pipe?**

A parameterized pipe in Angular allows you to pass arguments to a pipe for custom transformations. For example, in `{{ value | date:'short' }}`, `date` is the pipe, and `'short'` is the parameter.

**What are custom elements?**

Custom elements are a web standard for defining new HTML tags using the browser's built-in APIs. Angular allows you to create custom elements from Angular components, which can then be used in any web application.

**Do I need to bootstrap custom elements?**

No, custom elements do not need to be bootstrapped like Angular components. Once defined and registered with the browser, they can be used directly in the HTML.

**How do you define typings for custom elements?**

Typings for custom elements can be defined using TypeScript interfaces, where you specify the properties and methods that the custom element exposes. This helps in providing type safety when using custom elements in Angular or other TypeScript projects.

**Explain how custom elements work internally.**

Custom elements work by extending the `HTMLElement` class and defining the element's behavior in its lifecycle methods like `connectedCallback`, `disconnectedCallback`, `attributeChangedCallback`, etc. Angular provides tools to convert Angular components into custom elements, making them compatible with the Custom Elements API.

**How to transfer components to custom elements?**

To transfer Angular components to custom elements, you use the `@angular/elements` package, which wraps the component logic and turns it into a custom element that can be used in any HTML page.

**What are the mapping rules between Angular components and custom elements?**

The mapping rules between Angular components and custom elements include:
1. **Inputs:** Component @Input properties become attributes on the custom element.
2. **Outputs:** Component @Output events are exposed as custom events.
3. **Lifecycle:** Angular component lifecycle hooks are mapped to the custom element lifecycle callbacks.

**How are observables different from promises?**

Observables are more powerful than promises because:
1. **Multiple Values:** Observables can emit multiple values over time, while promises resolve only once.
2. **Lazy Execution:** Observables are lazy; they only execute when subscribed to, while promises execute immediately.
3. **Operators:** Observables support operators like `map`, `filter`, `merge`, etc., which makes it easier to work with streams of data.

**What is a custom pipe?**

A custom pipe in Angular allows you to create your own transformation logic for displaying data. You define a custom pipe by implementing the `PipeTransform` interface and decorating the class with `@Pipe`.

**Give an example of a custom pipe.**

```typescript
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({ name: 'exclaim' })
export class ExclaimPipe implements PipeTransform {
  transform(value: string): string {
    return value + '!';
  }
}
```
This custom pipe adds an exclamation mark to a string.

**What is the difference between pure and impure pipe?**

- **Pure Pipe:** A pure pipe only executes when the input data changes. It is stateless and does not cause performance issues.
- **Impure Pipe:** An impure pipe executes every time change detection runs, regardless of input changes. It can lead to performance issues but is useful in cases where the pipe's output depends on external factors.

**What is a bootstrapping module?**

A bootstrapping module in Angular is the root module that Angular uses to bootstrap the application. It typically includes the `@NgModule` decorator, which defines the components, directives, and services that the app will use. The `bootstrap` array in this module specifies the root component to load.

**Explain how to use HttpClient with an example.**

HttpClient is used in Angular to make HTTP requests. Here’s a simple example:

```typescript
import { HttpClient } from '@angular/common/http';
import { Injectable } from '@angular/core';
import { Observable } from 'rxjs';

@Injectable({
  providedIn: 'root',
})
export class DataService {
  constructor(private http: HttpClient) {}

  getData(): Observable<any> {
    return this.http.get('https://api.example.com/data');
  }
}
```

**What are lifecycle hooks in Angular?**

Lifecycle hooks are methods that Angular calls at different stages of a component's lifecycle:
1. **ngOnInit:** Called after the component is initialized.
2. **ngOnChanges:** Called when input properties change.
3. **ngDoCheck:** Called during change detection.
4. **ngOnDestroy:** Called before the component is destroyed.

**What are templates?**

Templates in Angular are HTML views where you define the structure and layout of the component. Templates use Angular's binding syntax, directives, and expressions to display dynamic data.

**How can you read the full response?**

To read the full response, including headers, status code, etc., you can use the `observe` option in the `HttpClient` method:

```typescript
this.http.get('https://api.example.com/data', { observe: 'response' })
  .subscribe(response => {
    console.log(response.headers);
    console.log(response.status);
    console.log
(response.body);
  });
```

**How do you perform Error handling?**

Error handling in Angular can be done using `catchError` in RxJS operators or by handling errors in the component:

```typescript
import { catchError } from 'rxjs/operators';
import { throwError } from 'rxjs';

this.http.get('https://api.example.com/data')
  .pipe(catchError(error => {
    console.error('An error occurred:', error);
    return throwError(error);
  }))
  .subscribe(data => {
    console.log(data);
  });
```

**What is content projection?**

Content projection allows you to insert dynamic content into a component using `<ng-content>`. It is useful for creating reusable components with customizable content.

**What is the difference between PROMISE & OBSERVABLES?**

The difference includes:
- **Promises:** Handle a single value, resolve once, and are eager (execute immediately).
- **Observables:** Handle multiple values, are lazy (execute only when subscribed to), and provide operators for transformation and composition.

**What do you mean by data binding?**

Data binding refers to the synchronization between the component’s data and the template. It ensures that changes in the component data are reflected in the view and vice versa.

**What do you mean by string interpolation?**

String interpolation is a way to bind data from the component to the template using double curly braces `{{ }}`. It allows dynamic data to be inserted into the HTML.

**What are the differences between Angular decorator and annotation?**

In Angular:
- **Decorator:** A function that adds metadata to classes, methods, properties, or parameters. Examples include `@Component`, `@Injectable`, etc.
- **Annotation:** A term used in older versions of Angular for what we now refer to as decorators. They are conceptually similar.

**What is an AOT compilation in Angular?**

Ahead-of-Time (AOT) compilation is the process of converting Angular HTML and TypeScript code into JavaScript code before the application is run in the browser. This results in faster rendering and fewer runtime errors.

**What are the advantages of AOT?**

Advantages include:
- **Faster Rendering:** Compiled code is faster to execute.
- **Smaller Bundle Size:** Unused code is removed during compilation.
- **Fewer Runtime Errors:** Errors are caught at compile time.

**What are the three phases of AOT?**

The three phases are:
1. **Parsing:** Angular parses the templates and TypeScript code.
2. **Compilation:** Angular compiles the code into JavaScript.
3. **Bundling:** The compiled code is bundled into a single or a few files for efficient loading.

**What are the components in Angular?**

Components are the building blocks of an Angular application. Each component consists of:
- **Template:** Defines the view.
- **Class:** Contains the logic.
- **Metadata:** Configures the component with decorators.

**What are dynamic components?**

Dynamic components are components that are created and inserted into the application at runtime, not at compile time. This allows for more flexible and reusable components.

**What is the purpose of the base href tag?**

The `<base href>` tag in the `index.html` file sets the base URL for all relative URLs in the application. It helps Angular handle routing correctly.

**What are modules in Angular?**

Modules are containers for a cohesive block of code dedicated to a particular application domain, workflow, or feature. Modules help organize an Angular application into manageable pieces.

**What is DOM?**

DOM (Document Object Model) represents the structure of an HTML document as a tree of nodes. Angular interacts with the DOM to update the view based on the data.

**What are services in Angular?**

Services are singleton classes used to encapsulate business logic, data access, or other functionalities that can be shared across components. They are injected into components and other services.

**What is two-way data binding?**

Two-way data binding allows synchronization of data between the component and the view. Changes in the view are reflected in the component, and changes in the component are reflected in the view, achieved using `[(ngModel)]`.

**What are pipes in Angular?**

Pipes are used to transform data in templates. Angular provides built-in pipes like `DatePipe` and `CurrencyPipe`, and you can also create custom pipes.

**What are observables in Angular?**

Observables are a way to handle asynchronous data streams. They provide methods to subscribe to data changes and process multiple values over time. Angular uses RxJS to handle observables.

**How do you chain pipes?**

You can chain pipes in Angular templates by using the pipe operator (`|`). For example, `{{ value | date | uppercase }}` applies the `date` pipe followed by the `uppercase` pipe.

**What does Angular Material mean?**

Angular Material is a UI component library for Angular that provides reusable, well-designed components following Material Design principles.

**What is RxJS?**

RxJS (Reactive Extensions for JavaScript) is a library for reactive programming using observables. It provides operators to work with asynchronous data streams and handle events.

**What is bootstrapping?**

Bootstrapping is the process of initializing and starting an Angular application. It involves loading the root module and component to kick off the application.

**What do you mean by dependency injection?**

Dependency injection (DI) is a design pattern used to implement IoC (Inversion of Control). It allows Angular to provide dependencies to classes, such as services, rather than having the classes create their own dependencies.

**What is the digest cycle process in Angular?**

The digest cycle is Angular’s way of checking for changes in the application. During each cycle, Angular compares the current and previous values of data-bound properties and updates the DOM if any changes are detected.

**What are the distinct types of Angular filters?**

Angular uses pipes instead of filters. Pipes include `DatePipe`, `CurrencyPipe`, `DecimalPipe`, etc., for formatting data in the view.

**How can one create a service in Angular?**

You can create a service in Angular using the Angular CLI:

```bash
ng generate service my-service
```

This creates a service file with a class decorated with `@Injectable()`, allowing it to be injected into components or other services.

**What is an Angular Router?**

Angular Router is a module that allows navigation between different views or components in a single-page application. It helps in setting up routes and handling client-side navigation.

**What is the purpose of the common module in Angular?**

The CommonModule provides common directives like `ngIf`, `ngFor`, and pipes like `DatePipe` and `CurrencyPipe` used in Angular applications. It is typically imported in feature modules.

**What is the scope of Angular?**

Angular’s scope refers to its capability to build web applications with rich user interfaces, client-side routing, and dependency injection. Angular is designed for building single-page applications with a component-based architecture.

**How do you create directives using CLI?**

You can create a directive using Angular CLI with:

```bash
ng generate directive my-directive
```

This generates a directive file with the necessary boilerplate code.

**What is a rule in Schematics?**

A rule in Schematics is a function that performs operations on a set of files. Rules can modify files, add new files, or perform other tasks to customize code generation.

**What is Schematics CLI?**

Schematics CLI is a tool that helps you create and manage Angular project templates and scaffolding. It provides commands to generate or modify code according to predefined templates.

**What is HttpClient, and what are its benefits?**

`HttpClient` is a service in Angular for making HTTP requests. Benefits include:
- Simplified API for handling HTTP operations.
- Integration with RxJS for handling asynchronous data.
- Built-in support for request and response transformation.

**What is multicasting in Angular?**

Multicasting in Angular refers to sharing a single observable subscription among multiple subscribers. This can be achieved using RxJS operators like `share()` or `publish()`.

**What is a directive in Angular?**

A directive is a class that allows you to add behavior to elements in the DOM. Directives can be structural (like `*ngIf`), attribute-based (like `ngClass`), or custom directives that you define.

**What will happen if you do not supply a handler for an observer?**

If you do not supply a handler for an observer, the observable will not perform any action or respond to data changes. The `next`, `error`, and `complete` methods should be provided to handle the emitted values, errors, and completion signals.

**What are angular elements?**

Angular Elements are Angular components that have been converted into custom elements (web components) using Angular’s `@angular/elements` package. They can be used in non-Angular applications or with other frameworks.

**What is the browser support of Angular Elements?**

Angular Elements are supported in modern browsers, including Chrome, Firefox, Safari, and Edge. They work on browsers that support the Custom Elements and Shadow DOM specifications.

**What is the role of SPA in Angular?**

SPA (Single Page Application) in Angular means that the application loads a single HTML page and dynamically updates the content as users interact with the app, providing a smoother user experience without full page reloads.

**What are Angular building blocks?**

Angular building blocks include:
- **Modules:** Organize application functionality.
- **Components:** Define views and logic.
- **Services:** Encapsulate business logic.
- **Directives:** Add behavior to DOM elements.
- **Pipes:** Transform data for display.


**Explain the MVVM architecture.**

MVVM (Model-View-ViewModel) is an architectural pattern where:
- **Model:** Represents the data and business logic of the application.
- **View:** Represents the UI or the presentation layer, which displays the data.
- **ViewModel:** Acts as an intermediary between the Model and the View. It handles the logic for fetching and manipulating data, as well as updating the View.

In Angular, components often play the role of the ViewModel, binding the View (template) with the Model (service or data).

**Describe Angular authentication and authorization.**

- **Authentication:** Involves verifying a user's identity, usually via a login process where the user provides credentials (e.g., username and password). Angular can manage authentication using services like `AuthService` and libraries like `AngularFire` or `Auth0` for handling authentication flows.

- **Authorization:** Determines what an authenticated user is allowed to do within the application. Angular can implement authorization using route guards (`CanActivate`, `CanLoad`) to restrict access to certain routes based on the user’s role or permissions.

**Explain the different kinds of Angular directives.**

Angular directives are categorized into three types:
1. **Component Directives:** These directives are created using the `@Component` decorator. They have their own template and can be used to build UI components.
2. **Structural Directives:** These change the structure of the DOM by adding or removing elements. Examples include `*ngIf`, `*ngFor`, and `*ngSwitch`.
3. **Attribute Directives:** These change the appearance or behavior of an element. Examples include `ngClass`, `ngStyle`, and custom attribute directives.

**What are the different types of compilers used in Angular?**

Angular uses two types of compilers:
1. **JIT (Just-In-Time) Compiler:** Compiles Angular code in the browser at runtime. This method is useful during development because it allows for faster rebuilds.
2. **AOT (Ahead-Of-Time) Compiler:** Compiles Angular code during the build process, before the browser loads it. This method is typically used in production to reduce the size of the application and improve performance.

**What is server-side rendering in Angular?**

Server-side rendering (SSR) in Angular refers to the process of rendering Angular applications on the server instead of the client. This is done using Angular Universal, which pre-renders pages on the server and sends the HTML to the client. This improves the performance and SEO of the application.

**What is Angular Universal?**

Angular Universal is a technology for SSR (Server-Side Rendering) in Angular. It allows Angular applications to be rendered on the server and delivered to the client with fully pre-rendered HTML, which enhances performance and SEO.

**What are HttpInterceptors in Angular?**

`HttpInterceptors` in Angular are a powerful way to modify outgoing HTTP requests or incoming responses. They are used to implement features like adding authentication tokens, logging, handling global errors, etc.

**How does one share data between components in Angular?**

Data can be shared between Angular components in several ways:
1. **Input/Output Properties:** Pass data from a parent component to a child component using `@Input` and emit events from the child component using `@Output`.
2. **Services:** Use a service to store and manage shared data, and inject it into the components that need access to it.
3. **State Management:** Use a state management library like NgRx or Akita to manage application-wide state.

**What is the difference between interpolated content and the content assigned to the innerHTML property of a DOM element?**

- **Interpolated Content (`{{}}`):** Angular sanitizes the content to prevent XSS attacks, ensuring that any inserted values are safe.
- **`innerHTML` Property:** Directly inserts HTML into the DOM. Angular sanitizes the HTML before it is inserted, but it can still be less safe if not handled properly.

**What is `ng-content` and its purpose?**

`ng-content` is a directive used for content projection in Angular. It allows you to insert external content into a component's template. For example, it enables the creation of reusable components like modals or tabs, where the content can vary depending on where the component is used.

**What is `ngcc`?**

`ngcc` (Angular Compatibility Compiler) is a tool that converts Node.js packages written with the Angular View Engine to the Ivy format. It allows legacy libraries to be used with Angular’s Ivy compiler.

**What is folding?**

In Angular, folding refers to the process of simplifying the Abstract Syntax Tree (AST) during AOT compilation. It involves evaluating expressions and resolving constants at compile time to optimize the output.

**What are macros?**

In Angular, macros refer to a simplified way of performing operations or creating reusable code blocks. They aren’t a built-in Angular feature but are often used in Angular’s build tools or configuration files for repeating tasks or simplifying complex setups.

**What is the state function?**

The `state` function in Angular animations is used to define different states of an element. You can specify styles for each state, and Angular will transition between these states when triggered.

**What is `Style()`?**

`Style()` in Angular animations defines the CSS styles to be applied during the animation. It can be used to set styles at the beginning, during, or at the end of an animation sequence.

**What is `NgZone`?**

`NgZone` is a service in Angular that helps manage change detection by running code outside or inside of Angular’s zone (the area where Angular automatically detects changes). It’s useful for optimizing performance by reducing unnecessary change detection cycles.

**What is `NoopZone`?**

`NoopZone` is a zone in Angular that does nothing (No-Operation). It is used to completely disable Angular's automatic change detection, typically for performance optimization in specific cases.

**How does Angular manage state?**

Angular manages state through services, which can hold and manage the application's state. For more complex state management, libraries like NgRx or Akita can be used. These libraries implement patterns like Redux to provide a more structured and scalable way to manage state across the application.

