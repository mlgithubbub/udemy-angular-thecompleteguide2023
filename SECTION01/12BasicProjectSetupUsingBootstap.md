# A Basic Project Setup using Bootstrap for Styling

- will often start with empty project for a given section to practice the topics from that section
1. use `ng new` to create a new angular project
2. start with an empty `app.component.html` file or if there is a different starting setup, you'll find it attached to lecture
3. remove `FormsModule` from app.module.ts to start with a clean slate:
    ```ts
    import { NgModule } from '@angular/core';
    import { BrowserModule } from '@angular/platform-browser';
    import { AppComponent } from './app.component';

    @NgModule({
    declarations: [
        AppComponent
    ],
    imports: [
        BrowserModule
    ],
    providers: [],
    bootstrap: [AppComponent]
    })
    export class AppModule { }
    ```
4. will use Bootstrap CSS framework to have some nice CSS styles out of the box without having to write them

    ## Install Bootstrap

    - navigate to project folder and install Bootstrap version 3, the version used in this course
    ```
    npm install --save bootstrap@3
    ```
    - this will install it locally, not globally
    - this will download it and store it in the node_modules folder
    - To use this, make Angular aware of this styling package:
    - go to `angular.json` 
    - go to the styles array
    - there is already one entry `styles.css`: files to define global styles to use application-wide in every angular component
    - add another entry before `styles.css` to override
        - node_modules > bootstrap > dist > css > `bootstrap.min.css`
        ```json
        "styles": [
                "node_modules/bootstrap/dist/css/bootstrap.min.css",
                "src/styles.css"
                ],
        ```
    - save the file and rerun `ng serve` to load the new configuration
    - open **developer tools** and go to **elements tab**, in **head** section you can see styles.css file is being imported
    - if you go to **sources** you can find the styles.css file, and it mentions Bootstrap there, so everything worked and Bootstrap is included
5. go to `app.component.ts` and get rid of any properties there
    ```ts
    export class AppComponent {
    }
    ```
