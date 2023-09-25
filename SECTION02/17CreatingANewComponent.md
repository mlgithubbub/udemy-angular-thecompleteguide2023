# Creating a New Component

- AppComponent is in the app module in the bootstrap array, which tells angular that it is a special component and you should bootstrap the whole application with that component as the root component
- All other components' selectors are not added to the index.html file but to the app.component.html file, because this is now the root component where we add the other parts

# Add a Component

1. Create new subfolder in the app folder called `server` because it will hold the server component
    - all app-related content goes into the app folder
    - it's good practice to have the folder name equal the component name
    - each component should have its own folder (not a hard rule, but makes sense)
