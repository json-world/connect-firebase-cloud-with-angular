# Connect Firebase with Angular 8/9/10 application

For all the developers who have been searching for a robust platform for building mobile and web application faster, you can think about Firebase. The Firebase is a Backend-as-a-Service that offers the developers a wide spectrum of tools and services to develop high-quality apps at a much faster pace.

In this article, We will see how to create a sample application to show how we can connect Firebase with Angular 8 Application.
**Note: The article has been written for Firebase version(NPM) of 6.6.1 and NPM version 5.2.1 of Angular Fire , So below mentioned approach may not work for very recent versions(7+).**

## Create Angular application using angular CLI
```
ng new connect-firebase-cloud-with-angular
```

## Set up Google Firebase account
For managing the stuffs at Firebase end, go to the Firebase and login using the gmail credentials. Once you navigate on the previous link, You will see a button to create a project. Click on that button then a form will open like below. Choose the name of your project and click on continue.

![Create Firebase Project](https://jsonworld.com/images/create-firebase-app.png)

After clicking the Continue button, Step 2 and Step 3 will come just click on the Continue button on these steps after checking on the checkboxes.

 

Once Project Setup is done, On the dashboard page naviage to project settings after clicking on settings icon at the top left. Required firebase credentials can be found from that page. Below credentials are required:

```
firebaseConfig: {
apiKey: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
authDomain: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
databaseURL: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
projectId: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
storageBucket: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
messagingSenderId: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
}
 
```

## Install Require NPM package and setup firebase with Angular

Install Firebase and AngularFire using NPM. Run the below command over the terminal.

```
npm install firebase @angular/fire --save
```

Add the Firebase credentials to environment.ts and environment.prod.ts file of the Angular project. After adding the firebase credentials, the file will look like below:

```
export const environment = {
production: false,
firebaseConfig: {
apiKey: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
authDomain: "http://localhost",
databaseURL: "https://xxxxxxxxxxxxxx.firebaseio.com",
projectId: "xxxxxxxxxxxx-8e0a7",
storageBucket: "xxxxxxxxxxxxxxxxx",
messagingSenderId: "xxxxxxxxxxxxxx"
}
 
};
```


Now, import AngularFireModule and the environment in app.module.ts file, then add AngularFireModule into the imports array. Now app.module.ts file look like below:

 ```
 import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
 
import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
 
// Firebase
import { AngularFireModule } from '@angular/fire';
import { environment } from '../environments/environment';
import { AngularFirestoreModule } from '@angular/fire/firestore';

import { AngularFireStorageModule } from '@angular/fire/storage';

import { AngularFireAuthModule } from '@angular/fire/auth';
 
@NgModule({
declarations: [
AppComponent
],
imports: [
BrowserModule,
AppRoutingModule,
AngularFireModule.initializeApp(environment.firebaseConfig, 'mytestapp'),
AngularFirestoreModule, // Only required for database features
AngularFireAuthModule, // Only required for auth features,
AngularFireStorageModule // Only required for storage features
],
providers: [],
bootstrap: [AppComponent]
})
export class AppModule { }
 ```
 
 
 **Note:** For only connecting the Angular app with firebase, AngularFireModule is required. And is also enough for using the Firebase database with the Angular app. Another firebase module added above is for other different purposes mentioned in the comments across the module in imports.
 
## Conclusion
In this article, We are done with how to connect Firebase with Angular 8 Application from scratch with firebase account setup.

Article was originally posted at [jsonworld.com](https://jsonworld.com/demo/how-to-connect-firebase-with-angular-8-application)
Read more articles on Firebase at [JsonWorld](https://jsonworld.com/firebase)
