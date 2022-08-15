# Examen Angular - Vueling University  - Constanza Ludueña 

This project was generated with Angular CLI version 14 and Bootstrap 5 using the approach Mobile First by sketching the web app's design for the smallest screen first and gradually working up to larger screen sizes. It has a development environment configured, including build, routing history, simple components, services, models and internationalization. This app is deployed on Heroku with Node and Express. In order to access the project through Heroku, you can click on the next link:

LINKKKKKKKKKKKKKKKKKKK DE HEROKUUUUU

****

## Table of Contents

- Project structure
- Installed versions
- Code scaffolding
- Scaffolding
- Development server
- Deploy on Heroku
- SASS
- Routes
- Internationalization with ngx-translate
- Navigation history
- Lazy loading
- Dependency injection
- Firebase
- Toastr

****

## Project structure

![Image](/assets/images/project-structure.png)

I have implemented this project structure based on everything I learned in the Vueling Univeristy program and I have tryed to follow the best practices according to the official Angular Documentation.

As it can be observed, src is made up by four main folders and app-component:

- Components --> this folder contains all the project components
- Core --> this one contains interfaces, enums, models and services
- Shared --> core functions which will be globally used across the application
- Styles --> scss styles foldes containing mixins, color variables or global classes
- App-components --> in the app-routing routes are defined and router-outlet is implanted into app-html. All new components are declared and imported in the app-module.

Apart from src, the assets folder contains images and json translations.


## Installed versions

 1. node -->16.15.1
 2. npm --> 8.11.0
 3. Angular --> 14.0.5
 4. Angular Material --> 14.0.4
 5. Express --> 4.18.1
 6. TypeScript --> 4.7.2
 7. Operative system --> Windows 10
 8. Dependency Injection
 
## Installation
 
 1. Download the repository zip or clone this repository to your own folder with the following command: git clone project-URL
 2. Install the dependencies at the root of your project with the following command: npm i or npm install
 3. Compile it running the following command: ng build
 
## Code scaffolding
 
Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.
 
##Scaffolding
 
 The next scaffolding has been used to start the project --> LINKKKKKKKKKKKKKKKKKKK
 
## Development server
 
Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.
 
### Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

### Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

### Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

### Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.

## Deploy on Heroku

In order to deploy the app on Heroku, node and express must be installed. Node helps Heroku to run the app. The file `server.js` needs to be created to make the connection to Heroku. The  `ng serve` command is only required for development, which is why a real server is needed for our production environment. 

### Actions to deploy my app to Heroku

* Create a new app on Heroku website.
* Setup Automatic Deployment from GitHub to Heroku.
* Connect to Github (Deploy method).
* Search your repo.
* Under Automatic Deploys, select the master branch and click Enable Automatic Deploys.
* Under Manual Deploys, click Deploy Branch. This is to push our fresh code to heroku.
* Settings, click Add Buildpack and select node.js

And now, configure Your Angular App to Deploy Properly on Heroku
* install express.js server with this command:
```
npm i express --save
```
* Create server.js file with this configuration:
```
let express = require('express');

let app = express();

app.use(express.static(__dirname+'/dist/angular-project'));

app.get('/*', (req, resp)=>{
  resp.sendFile(__dirname+'/dist/angular-project(index.html');
});

app.listen(process.env.PORT || 8080);
```
*  Go to package.json and change the scripts:
```
"start": "node server.js",
 "heroku-postbuild": "ng build"
 ```
* To make sure it works, build in your locale machine with the following command:
```
ng build
```
* And run you app:
```
npm start
```
* When the server is live, go to localhost:8080, and you can see that angular application is working correctly.
* Commit and push this changes.
* Heroku will automatically detect these changes, and the deploy will start.
* If you go to Overview section you will see that build is in progress.

The following tutorial was of great help: https://www.youtube.com/watch?v=XQdlMwS-azI

##SASS

The following sass style sheets have been created in order to use across the app.

- Variables to define main colors
- Mixins 
- Global classes

Apart from the style sheets created in order to organize the styling content which is used across the app, nesting has also been used in order to make the code clear.

## Routes

Routes are declared in `app-routing.module` and the respective routerLink is omplemented.

IMAGENNNNNNNNNNNNN DE UNA LINEA DE DIV ROUTERLINK

## Internationalization with ngx-translate

This project makes use of internationalization, which means that it is possible to navigate through ethe different languages with the library <ngx-translate>. This library allows the developer to define translations for the content in different languages and switch between them easily. In this case, `TranslationService` is used. It is used in the following way:

IMAGENNNNNNNNNNNNNNNNN DE UNA LINEA CON LA PIPE TranslateModule

Translations are stored in different JSON file for the different languages which are used.

IMAGENNNNNNNN DE LOS JSON

### Steps to use ngx-translate

Step 1: Add ngx-translate your Angular application
Enter the following line in the terminal: npm install @ngx-translate/core @ngx-translate/http-loader
The @ngx-translate/core contains the core routines for the translation: The TranslateService, the translate pipe and more. The @ngx-translate/http-loader loads the translation files dynamically from your webserver.

Step 2: Set up the TranslateModule and TranslateService
Start by initializing the TranslateModule in your app.module.ts.
Then switch to app.component.ts and add TranslateService to the constructor parameters to make it available in the component. Set the default language of your application using translate.setDefaultLang('es'). Set the current language to Spanish by calling translate.use('es').

Step 3: Create your JSON translation file (nested JSON preferably) and add them to a folder (within assets) named i18n.

Step 4: Use translations in your templates and code

Step 5: Switching languages at runtime
Add a simple language switcher:
	<button (click)="useLanguage('en')">en</button>
	<button (click)="useLanguage('de')">de</button>
Add the following method to the app.component.ts

	useLanguage(language: string): void {
    	this.translate.use(language);
	}

The following tutorial was of great help to me: https://www.codeandweb.com/babeledit/tutorials/how-to-translate-your-angular-app-with-ngx-translate

## Navigation history

As users, when we are navigating the app, every time we get a new URL address, we get a new page. This URL is saved in the browser history, which can is used to go back to the previous page. In the `NavigationService`, the route history is stored and we subscribe to events of the route change. Every route is saved in an array. It is important to note that this service contains a method to get the previous route and go back. We need to initialize the navigation service where we subscribe to a route change.

IMAGE OF LINES DEL GO BACK BUTTON CON LA FUNCION CLICKKKKK

## Lazy loading

Lazy loading was implemented in order to keep initial bundle sizes smaller, which in turn helped decrease load times. 
In order to check that a module is indeed being lazy loaded with the Chrome developer tools, you need to open the developer tools by pressing <Cmd+Option+i> on a Mac or <Ctrl+Shift+j> on a PC and go to the Network Tab. Click on the Orders or Customers button. If you see a chunk appear, everything is wired up properly and the feature module is being lazy loaded. A chunk should appear for Orders and for Customers but only appears once for each.

### Progress spinner

A progress or loader spinner is a branded element with a looping animation that indicates loading is in process and where it will appear. It displays the progress of an ongoing process by animating the indicator along a fixed invisible circular track in a clockwise direction. i.e., mat-progress-spinner is a circular progress indicator.

`mat-progress-spinner` is part of angular material module called MatProgressSpinnerModule and it was implemented so that once the user has entered his/her email address and password to access the website, the spinner appears for some miliseconds to let to know the user that the data is being checked.

## Dependency Injection

Dependencies are services or objects that a class needs to perform its function. In this project, I have implemented Dependency Injection, which is a design pattern in which a class requests dependencies from external sources rather than creating them in order to increase flexibility and modularity in the app.

### Creating an injectable service

In order to create a new Service class in the src/app directory, use the following command: ng generate service services/name-of-the-service, which will create automatically a new service in the project scaffoling.
The @Injectable() decorator specifies that Angular can use this class in the DI system. The metadata, providedIn: 'root', means that the service is visible throughout the application.

### Injecting services

To inject a dependency in a component's constructor(), supply a constructor argument with the dependency type. 

## Firebase

Firebase was used in order to carry out user authentication via Email & password. This library is a Google product which support different types of user authentication, among other things, for instance via Foofle, Facebook, Twitter, Github, etc and it doesn’t require server-side backend programming language.

In order to work with this library, Node.js and Angular CLI must be installed. Then the Firebase Account must be set up and a new Project must be created. Once this is all done with setting up the angular project and firebase account, it’s time to install AngularFire and Firebase from NPM with this command `npm install firebase @angular/fire --save`. 

In `src/environments/enviorment.ts` and `enviorment.prod.ts` files in your project folder. Then add your firebase configuration details in both the environment files as given below. Import AngularFireModule and environment in app.module.ts file, then declare AngularFireModule into the imports array.

Authentication is carried out through email and password. The user has the possibility of signing up as a new user with the email account and creating a password of a minimum of 8 characters containing at least one number and one letter. Then, the user can log in and get full access to the website content. In case the user ever forgives his/her password, there is an option to reset it through the email address provided.  

There are multiple users already created, which were used to test this functionality. To try it out, it´s possible to enter the following user and password:
Email: constanza@gmail.com 
Password: coti1234

## Toastr

Toastr is a Javascript library for non-blocking notifications which lets you create highly customizable toast messages on your webpage.

In order to use it, download and include the jQuery Toastr plugin's files into your webpage which has jQuery library installed.

<link href="toastr.css" rel="stylesheet">
<script src="//code.jquery.com/jquery.min.js"></script>
<script src="toastr.js"></script>

These are the default toast messages that are available to diplay:

// with no title
toastr.warning('Warning')
toastr.success('Success')
toastr.info('Info')

// with a title
toastr.error('Error','Error Title')


## Author

Constanza Ludueña

- Linkedin: www.linkedin.com/in/constanza-luduena
- GitHub: https://github.com/constanzaludu