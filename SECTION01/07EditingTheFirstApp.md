# Editing the First App

1. get an IDE or editor to write and edit your code
    - WebStorm is grea for Angular, but not free, a free option is: Visual Studio code
2. Look at all the folders and files the Angular CLI created for you 
    - Most of the files are just doing some configuration and you don't need to touch them
    - One interesting file is `package.json`, where you can see all the dependencies such as angular 16.2
    - `devDependencies` are only required for development, for the build workflow

## Edit Our Code

3. Jump into source folder
    - e2e: end to end testing
    - node_modules: where dependencies were actually installed
    - keep ng serve running because it automatically rebuilds your project whenever you change and save something
    - when you're done developing for the day, quit with control + c

4.  Open src > app > app.component.html

    ```html
    <div style="text-align:center">
    <h1>
        Welcome to {{ title }}!
    </h1>
    <img width="300" alt="Angular Logo" src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNTAgMjUwIj4KICAgIDxwYXRoIGZpbGw9IiNERDAwMzEiIGQ9Ik0xMjUgMzBMMzEuOSA2My4ybDE0LjIgMTIzLjFMMTI1IDIzMGw3OC45LTQzLjcgMTQuMi0xMjMuMXoiIC8+CiAgICA8cGF0aCBmaWxsPSIjQzMwMDJGIiBkPSJNMTI1IDMwdjIyLjItLjFWMjMwbDc4LjktNDMuNyAxNC4yLTEyMy4xTDEyNSAzMHoiIC8+CiAgICA8cGF0aCAgZmlsbD0iI0ZGRkZGRiIgZD0iTTEyNSA1Mi4xTDY2LjggMTgyLjZoMjEuN2wxMS43LTI5LjJoNDkuNGwxMS43IDI5LjJIMTgzTDEyNSA1Mi4xem0xNyA4My4zaC0zNGwxNy00MC45IDE3IDQwLjl6IiAvPgogIDwvc3ZnPg==">
    </div>
    <h2>Here are some links to help you start: </h2>
    <ul>
    <li>
        <h2><a target="_blank" rel="noopener" href="https://angular.io/tutorial">Tour of Heroes</a></h2>
    </li>
    <li>
        <h2><a target="_blank" rel="noopener" href="https://angular.io/cli">CLI Documentation</a></h2>
    </li>
    <li>
        <h2><a target="_blank" rel="noopener" href="https://blog.angular.io/">Angular blog</a></h2>
    </li>
    </ul>
    ```
5. Edit the heading
   ```html
    <h1>
        Welcome to {{ title }}!
    </h1>
    ```
    ```html
    <h1>
        Hi this {{ title }}!
    </h1>
    ```
    - `{{ title }}` is from Angular
    - Angular is not a tool to write static HTML files (we would need no framework for that), it allows us to mix static HTML code and dynamic things we want to output in that code
    - Angular works with components
    - The app.component is one of the components angular works with

A component always has:
- a template: html file: app.component.html
- possibly styling: CSS file: app.component.css
- a typescript file: app.component.ts

6. Open app.component.ts
    ```ts
    import { Component } from '@angular/core';

    @Component({
    selector: 'app-root',
    templateUrl: './app.component.html',
    styleUrls: ['./app.component.css']
    })
    export class AppComponent {
    title = 'my-first-app';
    }
    ```
    - This is the definition of the component
    - This will be compiled into normal JavaScript by the build workflow
- A couple interesting things here:
    1. `@Component`: we will explore later
    2. ```ts
        title = 'my-first-app';
        ```
        - This is related to `{{ title }}` in the html file
        - We can change it
        - This is called `data binding`
        - if you right-click on the loaded page and inspect page source you only see script imports at the bottom, not that code and the `<app-root>` tag
        - we also see `<app-root>` in the selector 
        ```ts
        @Component({
        selector: 'app-root',
        templateUrl: './app.component.html',
        styleUrls: ['./app.component.css']
        })
        ```
        - we are creating our own HTML tag
        - the page we are seeing is index.html:
        ```html
        <!doctype html>
        <html lang="en">
        <head>
        <meta charset="utf-8">
        <title>MyFirstApp</title>
        <base href="/">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <link rel="icon" type="image/x-icon" href="favicon.ico">
        </head>
        <body>
        <app-root></app-root>
        </body>
        </html>
        ```
        - the script imports are missing because they are injected dynamically
        - the script imports dynamically replace `<app-root>` with our own component

    
7. Delete contents of app.component.html
8. Add this code:
    ```ts
    <input type="text">
    <p>{{ name }}</p>
    ```
9. Go to app.component.ts and change `title` to `name` and set it equal to your name: 
    ```ts
    export class AppComponent {
    title = 'farts-a-lot';
    }
    ```
    ```ts
    export class AppComponent {
    name = 'Morgan';
    }
    ```
10. use an angular directive `ng model`
    ```html
    <input type="text" [(ngModel)]="name">
    <p>{{ name }}</p>
    ```
    - this tells Angular to listen to anything you enter here, store it in the name model and output it below
    - on the page we don't see anything, but if we open developer tools, we see an error: "can't bind to 'ngModel' since it isn't a known property of 'input'
    - Angular is made up of different modules and to use those features, we need to add them
    - To add the modules, go to `app.module.ts`, and import `FormsModule` (a typescript feature)
    - Add it to the imports array
    ```ts
    import { NgModule } from '@angular/core';
    import { BrowserModule } from '@angular/platform-browser';

    import { AppComponent } from './app.component';
    import { FormsModule } from '@angular/forms';

    @NgModule({
    declarations: [
        AppComponent
    ],
    imports: [
        BrowserModule,
        FormsModule
    ],
    providers: [],
    bootstrap: [AppComponent]
    })
    export class AppModule { }

    ```
    

