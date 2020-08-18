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
Angular Material
The [installation instructions](https://material.angular.io/guide/getting-started) are sufficient, with the following notes:
* Exit the Angular application prior to installing Angular Material; if you do not, the application compilation fails, you have to exit, remove `node_modules`, run `npm install` and restart the application;
* Use the `ng add @angular/material` installation option since it does all the work for you; note that I used `yarn` to install Angular Material, and had all kinds of problems, since Angular seems to depend on the `package.lock.json` file; hence, keep it simple and use the `ng add ...` command;
````shell script
$ ng add @angular/material
````
* Create a module to host all Material modules, and import into `app.modules`;
```typescript
import {NgModule} from '@angular/core';
import {A11yModule} from '@angular/cdk/a11y';
import {ClipboardModule} from '@angular/cdk/clipboard';
import {DragDropModule} from '@angular/cdk/drag-drop';
import {PortalModule} from '@angular/cdk/portal';
import {ScrollingModule} from '@angular/cdk/scrolling';
import {CdkStepperModule} from '@angular/cdk/stepper';
import {CdkTableModule} from '@angular/cdk/table';
import {CdkTreeModule} from '@angular/cdk/tree';
import {MatAutocompleteModule} from '@angular/material/autocomplete';
import {MatBadgeModule} from '@angular/material/badge';
import {MatBottomSheetModule} from '@angular/material/bottom-sheet';
import {MatButtonModule} from '@angular/material/button';
import {MatButtonToggleModule} from '@angular/material/button-toggle';
import {MatCardModule} from '@angular/material/card';
import {MatCheckboxModule} from '@angular/material/checkbox';
import {MatChipsModule} from '@angular/material/chips';
import {MatStepperModule} from '@angular/material/stepper';
import {MatDatepickerModule} from '@angular/material/datepicker';
import {MatDialogModule} from '@angular/material/dialog';
import {MatDividerModule} from '@angular/material/divider';
import {MatExpansionModule} from '@angular/material/expansion';
import {MatGridListModule} from '@angular/material/grid-list';
import {MatIconModule} from '@angular/material/icon';
import {MatInputModule} from '@angular/material/input';
import {MatListModule} from '@angular/material/list';
import {MatMenuModule} from '@angular/material/menu';
import {MatNativeDateModule, MatRippleModule} from '@angular/material/core';
import {MatPaginatorModule} from '@angular/material/paginator';
import {MatProgressBarModule} from '@angular/material/progress-bar';
import {MatProgressSpinnerModule} from '@angular/material/progress-spinner';
import {MatRadioModule} from '@angular/material/radio';
import {MatSelectModule} from '@angular/material/select';
import {MatSidenavModule} from '@angular/material/sidenav';
import {MatSliderModule} from '@angular/material/slider';
import {MatSlideToggleModule} from '@angular/material/slide-toggle';
import {MatSnackBarModule} from '@angular/material/snack-bar';
import {MatSortModule} from '@angular/material/sort';
import {MatTableModule} from '@angular/material/table';
import {MatTabsModule} from '@angular/material/tabs';
import {MatToolbarModule} from '@angular/material/toolbar';
import {MatTooltipModule} from '@angular/material/tooltip';
import {MatTreeModule} from '@angular/material/tree';
import {OverlayModule} from '@angular/cdk/overlay';

@NgModule({
    exports: [
        A11yModule,
        ClipboardModule,
        CdkStepperModule,
        CdkTableModule,
        CdkTreeModule,
        DragDropModule,
        MatAutocompleteModule,
        MatBadgeModule,
        MatBottomSheetModule,
        MatButtonModule,
        MatButtonToggleModule,
        MatCardModule,
        MatCheckboxModule,
        MatChipsModule,
        MatStepperModule,
        MatDatepickerModule,
        MatDialogModule,
        MatDividerModule,
        MatExpansionModule,
        MatGridListModule,
        MatIconModule,
        MatInputModule,
        MatListModule,
        MatMenuModule,
        MatNativeDateModule,
        MatPaginatorModule,
        MatProgressBarModule,
        MatProgressSpinnerModule,
        MatRadioModule,
        MatRippleModule,
        MatSelectModule,
        MatSidenavModule,
        MatSliderModule,
        MatSlideToggleModule,
        MatSnackBarModule,
        MatSortModule,
        MatTableModule,
        MatTabsModule,
        MatToolbarModule,
        MatTooltipModule,
        MatTreeModule,
        OverlayModule,
        PortalModule,
        ScrollingModule,
    ]
})
export class AppMaterialModule {}
```
* Re-factor `tsconfig.app.json` to include the files we will create:
```json
{
  "extends": "./tsconfig.base.json",
  "compilerOptions": {
    "outDir": "./out-tsc/app",
    "types": []
  },
  "include": ["src/**/*", "src/**/*.d.ts"],
  "exclude": ["node_modules", "**/*.spec.ts"],
}
```
* Add the `<mat-slider min="1" max="100" step="1" value="1"></mat-slider>` element to the `app.component.html` right below the `Here are some resources to help your get strated`;
* Observe the `slider` showing up in your app;
* Remove the `slider`;
* Refactor the `ng e2e` script to run from port 4201, so that you can run it while the application is running;
* Run the unit, `yarn test`, and integration, `yarn e2e` tests to ensure all is well;

##Install Redux
Exit the application, run the installation scripts below, run the unit and integration tests, then get back to work.
* [Install](https://ngrx.io/guide/store/install) `*ngrx/store`:
```shell script
$ ng add @ngrx/store@latest --minimal false
```
* [Install](https://ngrx.io/guide/effects/install) `*ngrx/effects`:
```shell script
$ ng add @ngrx/effects@latest --minimal false
```
 * This command will automate the following steps:
   * Update `package.json > dependencies` with `@ngrx/effects`.
   * Run `npm install` to install those dependencies.
   * By default will create a `src/app/app.effects.ts` file with an empty `AppEffects` class that has the `actions$: Actions` observable injected into it. If group flag is set to true then this file will be created under an effects folder.
   * Create a` src/app/app.effects.spec.ts` spec file with a basic unit test. If group flag is set to true then this file will be created under an effects folder.
   * Update your `src/app/app.module.ts > imports` array with `EffectsModule.forRoot([AppEffects])`. If you provided flags then the command will attempt to locate and update module found by the flags.
* [Install](https://ngrx.io/guide/store-devtools/install) `*ngrx/store-devtools`:
```shell script
$ ng add @ngrx/store-devtools@latest
```
 * This command will automate the following steps:
   * Update `package.json > dependencies` with `@ngrx/store-devtools`.
   * Run `npm install` to install those dependencies.
   * Update your `src/app.module.ts > imports` array with `StoreDevtoolsModule.instrument({ maxAge: 25, logOnly: environment.production })`. The `maxAge` property will be set to the flag maxAge if provided.

