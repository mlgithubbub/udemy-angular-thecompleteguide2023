# About the Course Code/ Code Snapshots

- Find the source code of each section attached to the last lecture of that section
- All the course code will only work if you are not using strict mode
- Strict mode forces you to write more verbose code in some places (esp. with regard to class properties)
- If you enabled strict mode by accident, diable it by setting `strict: false` in your `tyconfig.json` file

- Because of dependency version mismatches, running attachments might fail, so you can try the following:
1. Create a new project via `ng new my-project --strict false`
2. Copy the content of the ZIP attachement into the newly created project folder
3. Run your project with `ng serve`
- If you try to run ZIP attachments directly, you must run `npm install` first
- if you get errors while running `npm install`, try running `npm install --legacy-peer-deps` instead

Check out this thread if you have problems with the code (error msgs or don't know how to use it): https://www.udemy.com/the-complete-guide-to-angular-2/learn/lecture/6709112#questions/8079942