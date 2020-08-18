#The Action Required Application
##Introduction
This project's goal is to learn how to integrate [Redux](https://redux.js.org/) into [Angular](https://angular.io/) and [Angular Material](https://material.angular.io/).

A common learning tool for these kinds of projects is to write a `Todo` application using the target technologies. I'll do it, but will name the application `Action Required` since `todo` is a reserved word in my IDE.

I'll leverage the [Todo Application](https://github.com/RodrigoMattosoSilveira/react-springboot-todo) I wrote to learn [React](https://reactjs.org/), [Redux](https://redux.js.org/), [Material UI](https://material-ui.com/) and [Springboot](https://spring.io/projects/spring-boot).

I give a lot of credit to the work by the [Spring team contributors](https://github.com/spring-guides/tut-react-and-spring-data-rest/graphs/contributors), who wrote the excellent [React.js and Spring Data REST tutorial](https://spring.io/guides/tutorials/react-and-spring-data-rest/), showcasing a [React](https://reactjs.org/) as the front end and [Springboot](https://spring.io/projects/spring-boot) as the backend. 

Note that each of these technologies are very complex, rendering any effort to provide a short explanation useless. Therefore, you must have working experience with them before tackling this exercise! I'll assume you have and will reference concepts assuming so.
##Use Cases
The use cases are quite simple:
* An `Action Requested Item`, `AR` has the following attributes:
  * State - Whether it is `active` or `done`;
  * Text - A brief description of the expected result;
  * Priority - One of three choices, LOW/MEDIUM/HUGH, with LOW as the default;
  * Owner - The user that created it;
* The user can filter the list of `ARs` by:
  * Show all items, only `active`, or `done` `ARs`;
  * Showing any combination of `LOW/MEDIUM/HIGH` `ARs`;
  * The default is to show all `ARs`;
* The user creates an new `AR` by clicking on a `Create` button in list of filtered `ARs`; when an user creates a new `AR`, the application navigates to the last page;
* The user updates an existing `AR` by clicking on an attribute and editing it;
* The user deletes an existing `AR` by clicking on its `delete` button; when an user deletes an `AR`  the application navigates to the page showing the `AR` immediately preceding it;
* The user leverages the `Pagination menu` at the bottom of the `AR` list to configure the number of `ARs` per page; this menu includes options to select the number of items per page, to navigate to the first, previous, next, and lat pages;
* Users can view all `ARs` but only update or delete their own `ARs`;
* When a user updates or deletes an `AR`, all users receive notifications thereof;
##Foundational technologies
The foundational technologies that will support the effort are:
* [Angular](https://angular.io/) - it replaces [React](https://reactjs.org/) used in the original [Todo Application](https://github.com/RodrigoMattosoSilveira/react-springboot-todo);
* [@NGRX](https://ngrx.io/) - it replaces [react-redux](https://react-redux.js.org/) used in the original [Todo Application](https://github.com/RodrigoMattosoSilveira/react-springboot-todo);
* [Angular Material](https://material.angular.io/) - it replaces [Material UI](https://material-ui.com/) used in the original [Todo Application](https://github.com/RodrigoMattosoSilveira/react-springboot-todo);

#Installation
We will:
* Install [Angular](https://angular.io/);
* Create the [ng-rdx-mat-spring-ar application];(https://github.com/RodrigoMattosoSilveira/ng-rdx-mat-spring-ar)
* Install [Angular Material](https://material.angular.io/) 
* Install [@NGRX](https://ngrx.io/);

##Angular
You use the Angular CLI to create projects, generate application and library code, and perform a variety of ongoing development tasks such as testing, bundling, and deployment.

##Install the Angular CLI
To install the Angular CLI, open a terminal window and run the following command:
````shell script
$ npm install -g @angular/cli
````
##Create a workspace and initial application
You develop apps in the context of an Angular workspace. To create a new workspace and initial starter app, run the CLI command ng new and provide the name ng-rdx-mat-spring-ar, as shown here:

````shell script
$ ng new ng-rdx-mat-spring-ar
````
The `ng new` command prompts you for information about features to include in the initial app. Accept the defaults by pressing the `Enter` or `Return` key. The Angular CLI installs the necessary Angular npm packages and other dependencies. This can take a few minutes.bThe CLI creates a new workspace and a simple Welcome app, ready to run.
