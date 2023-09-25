# Project Setup and First App

- use official Angular CLI (command line interface)
- this is recommended way of creating Angular projects
- because Angular projects are more elaborate regarding build workflow
- a couple files need to be converted before they can be run in the browser and the CLI does that
- the CLI also optimized the code, so we ship optimized code to the browser when we deploy the app

## node.js & npm

- We won't be writing any node.js code, but node.js will be used behind the scenes by the CLI to bundle and optimize our project
- we will use npm to manage the different dependencies the project has, such as the Angular framework itself and other libraries it uses
1.  install node.js and npm: https://nodejs.org/en/download


## Run Angular Commands:


2. 
```
npm install -g @angular/cli
```
- `-g` means globally
- `@angular/cli/latest` latest is optional
- may have to add `sudo` at the beginning of command to give yourself the right permissions
3. Navigate to folder you want to create project, and then:
```
ng new my-dream-app --no-strict
```
- Note: Use any name but 1. no white spaces and 2. don't use the word test
- strict mode is a special mode to create projects
- to make things easier to get started, we'll start in non-strict mode
4. Would you like to add Angular routing? -> n
- not yet, we'll dive into this later in the course
5. Which stylesheet format would you like to use? -> CSS
- a new angular project will be created
- we need this more complex setup with all these dependencies because Angular uses Typescript, a superset of JavaScript, which is compiled down to JavaScript at the end
6. Navigate to the app and run ng serve to bring up a development server that will run your app so you can see it in the browser
```
cd my-dream-app

ng serve
```
- server runs on localhost:4200 by default
7. Download the app.component.zip file, unpack and drag the app.component.html file into: my-first-app -> src -> app and replace the current file there
8. reload localhost:4200 to follow along smoothly with the tutorial

