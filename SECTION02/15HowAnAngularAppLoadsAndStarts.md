# How an Angular App gets Loaded and Started

- Change the content of `app.component.html`:
```html

```
- How does our development server know it has to render the content of `app.component.html`?
- Is it because it is the only component we have now? No, and this is not the file served by the server
- The `index.html` file is served by the server, this is the single page served by the server

Look at the `index.html` file:
- In the body `<app-root>` The CLI created this component for us, it is the component that will tie our whole application together in the end
- all the files in the app folder, that have `app.component` in their name are related to the `app-root` component

Look at `app.component.ts` file
- it has an `@Component` decorator
- We have a `selector` property, which has the string `'app-root'` as the value

### How is Angular triggered to run-over the body of the index.html file?

- Inspect the source code again and see the script imports at the end
- These are injected by the CLI automatically, so you don't see them in the raw index.html file
- every time `ng serve` builds our project, it creates JS script bundles and automatically adds the right imports in the index.html file
- These script files contain our code, and are the first code to be executed

The code in `main.ts` is the first code that gets executed

1. bootstrap starts by passing an appmodule into this method
2. AppModule refers to `app.module.ts`
    - `@NgModule`
    - bootstrap array which lists all components which should be known to angular at the point of time it analyzes our index.html file

The whole process:
1. Angular gets started at main.ts
2. We bootstrap an angular application and pass this module as an argument: `app.module.ts`
3. In this module we tell Angular there is an AppComponent you should know about when you try to start yourself
4. Angular now analyzes the app.component.ts and reads the setup we pass here and knows the selector `app-root`
5. Now angular is able to handle `app-root` in the index.html file, it knows the selector from the bootstrap array in the app.module.ts, and it knows to insert the app component here
6. It knows the app component has HTML code attached to it
