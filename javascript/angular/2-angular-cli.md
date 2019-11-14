# 2. Angular CLI

`Angular CLI` helps with:

1. Bootstrapping \(or Initializing or Generating\) a new project
2. Serving and live reloading
3. Code generation
4. Building, Packaging and releasing
5. Testing

```typescript
// Instalation
npm install -g @angular/cli
ng -v

// ***** 1. Bootstrapping (or Initializing or Generating) a new project *****
/*
- It creates the initial project structure with a root NgModule and a root component and bootstraps it using the platformBootstrapDynamic method.
- The project is also configured to use the webpack loader which handles things like module loading, bundling and minification of dependant code.
*/

// Create New Angular App:
ng new myapp1


// ***** 2.Serving and live reloading *****
/*
- The CLI starts a local web-server so we can view our application in the browser via localhost:4000.
- The CLI also watches for any changes to our files and automatically reloads the webpage if there are any.
*/

// Run App:
ng serve

// ***** 3. Code generation *****
/*
- Using the CLI we can create components directives, services, pipes etc…​ all from the command line with all the necessary files, folders and boilerplate code included.
- All the generated code adheres to the official 'Angular style guide'.
*/


// ng generate <scaffold> <name>
ng generate component Header
// shortcut
ng g c Header

ng g component My 
// Creates MyComponent
// By default all generated files go in into src\app\my-component, a folder called my-component is created for us.


ng g directive My 
// Creates MyDirective
// By default all generated files go in into src\app, no folder is created.


ng g pipe My 
// Creates MyPipe
// By default all generated files go in into src\app, no folder is created.


ng g service MyService 
// Creates MyService
// By default all generated files go in into src\app, no folder is created.


ng g class MyClass
// Creates MyClass
// By default all generated files go in into src\app, no folder is created.
..... }//{....... 

ng g interface MyInterface 
// Creates MyInterface
// By default all generated files go in into src\app, no folder is created.
..... }//{....... 

ng g enum MyEnum 
// Creates MyEnum
// By default all generated files go in into src\app, no folder is created.
..... }//{....... 


// ***** 4. Building, Packaging and releasing *****
/*
- The CLI doesn’t just stop with development,
- using CLI we can also package our application ready for release to a server.
*/

// ###### 4.1 Create a new build:
ng build
// This bundles all our javascript, css, html into a smaller set of files which we can host on another site simply.

// It outputs these files into the dist folder:
.
├── assets
├── index.html
├── inline.js
├── inline.map
├── main.bundle.js
├── main.map
├── styles.bundle.js
└── styles.map

// copy dist folder and deploy in any http-server (it works)

// By default the ng build command creates a development build, no effort is made to optimise the code.

// Create a new (Production) build:
ng build --prod

// This might generate an output like the below:
.
├── assets
├── index.html
├── inline.js
├── main.3f26904b701596b6d90a.bundle.js
├── main.3f26904b701596b6d90a.bundle.js.gz
└── styles.b52d2076048963e7cbfd.bundle.js

// ###### 4.2 Running with ```--prod``` changes a few things:
/*
- The bundles now have random strings appended to them to enable **cache busting**.
    - This ensures that a browser doesn’t try to load up previously cached versions of the files and instead load the new ones from the server.
- The file sizes are much smaller. 
    - The files have been processed through a minifier and uglifier.
- There is a much small ```.gz``` file, 
    - this is a compressed version of the equivalent javascript file.
    - Browsers first try to download the ```.gz``` version of files (if they present)
*/

// ###### 4.3 Adding a third party module

// ###### 4.3.1 Library Installation (Angular Scope)
/*
- If we wanted to use any 3rd party libraries in Angular, 
    - we need to add as part package.json
- That way Angular knows about the libraries and includes them in the build process and bundles with the main application js files.
*/

/*
E.g. :
If we want to include a moment.js library to use in our Angular javascript code, we just need to install it via npm like so:
*/
// Install and --save (Adds into package.json)
npm install moment --save


// If we also want to include the typescript type definition file for our module we can install it via 'types':

npm install @types/moment --save

// Now when Angular create a build either when releasing or serving locally, the moment library is automatically added to the bundle.

// ###### 4.3.2 Library Installation (Global Scope)
/*
- Some javascript libraries need to be added to the **global scope** (not just to angular scope),
    - load them just like they were in a script tag.
- twitter bootstrap library is a great example of this,
    - we need to incldue css and script files in the global scope
*/

// Install (need not to save)
npm install bootstrap@next
// Add them in ```angular-cli.json
```

{ . . . "apps": \[ { . . . "styles": \[ "styles.css", "../node\_modules/bootstrap/dist/css/bootstrap.css" \], "scripts": \[ "../node\_modules/jquery/dist/jquery.js", "../node\_modules/tether/dist/js/tether.js", "../node\_modules/bootstrap/dist/js/bootstrap.js" \], . . . } \], . . . }

// Now when the build runs the CLI includes those files in the bundle and injects then in the global scope.

// **\*** 5. Testing **\***

// jasmine unit tests // - Whenever we generate Angular code, CLI also creates test files`.spec.ts`

// run all our unit tests with one command ng test

/\* This builds our project and then runs all the tests, any errors are output to the terminal.

This command also watches for any changes in our files and, if it detects any, re-runs the tests automatically. \*/

```text
```js
// ng help


ng new <options...>
  Creates a new directory and a new Angular app eg. "ng new [name]".
  aliases: n

ng serve <options...>
  Builds and serves your app, rebuilding on file changes.
  aliases: server, s

ng test <options...>
  Run unit tests in existing project.
  aliases: t

ng build <options...>
  Builds your app and places it into the output path (dist/ by default).
  aliases: b

ng lint <options...>
  Lints code in existing project.
  aliases: l




ng get <options...>
  Get a value from the configuration. Example: ng get [key]

ng set <options...>
  Set a value in the configuration.
  aliases: -g, --global  

ng e2e <options...>
  Run e2e tests in existing project.


ng completion <options...>
  Adds autocomplete functionality to `ng` commands and subcommands.
  aliases: e

ng doc <keyword> <options...>
  Opens the official Angular API documentation for a given keyword.

ng eject <options...>
  Ejects your app and output the proper webpack configuration and scripts.

ng generate <blueprint> <options...>
  Generates and/or modifies files based on a blueprint.
  aliases: g

ng version <options...>
  Outputs Angular CLI version.
  aliases: v, --version, -v

ng xi18n <options...>
  Extracts i18n messages from source code.

ng help <command-name (Default: all)>
  Shows help for the CLI.
```

