# Firebase

Firebase is a platform from Google for various mobile and web development, offering services such as NoSql databases, file storage, hosting, authentication, analyrics, ads, messaging, and more. Some of the services, such as databases and storage are free up to a certain limit, with more functions, speed, and storage space offered for paying tiers.

> :warning: **Due to [Googles Firebase controversies](https://archive.md/Zjpb1), it is not adviced to store personal information in the service.**

- [Project overview](https://console.firebase.google.com)
- [Firebases pricing tiers](https://firebase.google.com/pricing)
- [Local Emulator for testing/prototype/learning](https://firebase.google.com/docs/emulator-suite)

## NoSql database

Firebase offers two types of databases, from [the docs](https://firebase.google.com/docs/database/rtdb-vs-firestore)(which also helps you to pick):

- Cloud Firestore is Firebase's newest database for mobile app development. It builds on the successes of the Realtime Database with a new, more intuitive data model. Cloud Firestore also features richer, faster queries and scales further than the Realtime Database.
- Realtime Database is Firebase's original database. It's an efficient, low-latency solution for mobile apps that require synced states across clients in realtime.

## Kotlin+Maven connection

- [Helpful StackOverflow post](https://stackoverflow.com/questions/40799258/where-can-i-get-serviceaccountcredentials-json-for-firebase-admin)
- [Official guide](https://firebase.google.com/docs/database/admin/start#authenticate-with-admin-privileges)

Although an API is not the intended usecases for Firebase, not to even mentioning NoSql, since it has some use-cases for phone apps (Andriod apps, often developed in Kotlin) it is possible with some rigging.
First off all, this requires a set up database. For some reason, (Cloud) Firestore Database seems to be working best for this.

The following list of files and functionalities are required:
- A third party package for Firebase.
  - Maven: 
    - ```
      <dependency>
          <groupId>com.google.firebase</groupId>
          <artifactId>firebase-admin</artifactId>
          <version>7.0.0</version>
      </dependency>
      <dependency>
          <groupId>com.google.gms</groupId>
          <artifactId>google-services</artifactId>
          <version>3.1.1</version>
          <scope>runtime</scope>
      </dependency>
      ```
- A JSON string with the following keys and secrets:
  - ```
    {
        "type": "type",
        "project_id": "pId",
        "private_key_id": "pKeyId",
        "private_key": "pKey",
        "client_email": "cEmail",
        "client_id": "cId",
        "auth_uri": "aUri",
        "token_uri": "tUri",
        "auth_provider_x509_cert_url": "authUrl",
        "client_x509_cert_url": "clientUrl"
    }
    ```
  - These calues can be found in your Firebase app, by clicking the cog next to "Project Overview" top right, then "Project settings", under the tab "Service accounts". Click on "Generate new private key" which will download the JSON file with secrets to your device.
- A method that initializes Firebase and gets the instance of the app, early in the startup (after you read the secrets from your config-sources). In Kotlin, a class annotated with
``` @Primary @Component ``` with a constructor annotated with ``` @PostConstruct ``` should be enough.

## React+NPM connection

The following list of files and functionalities are required:
- A third party package for Firebase.
  - NPM:
    - ```
      "firebase": "^7.15.4"
      ```
- An object with the following keys and and secrets:
  - ```
    {
        apiKey: REACT_APP_FB_KEY,
        authDomain: REACT_APP_FB_DOM,
        databaseURL: REACT_APP_FB_URL,
        projectId: REACT_APP_FB_PID,
        storageBucket: REACT_APP_FB_SBU,
        messagingSenderId: REACT_APP_FB_SID
    }
    ```
  - These calues can be found in your Firebase app, by clicking the cog next to "Project Overview" top right, then "Project settings", under the tab "General".
- A method that initializes Firebase and gets the instance of the app, early in the startup (after you read the secrets from your config-sources). React has a App.js file with a class App, which has a constructor perfect for this.

## Database rules

TODO

```
service cloud.firestore 
{
  match /databases/{database}/documents 
  {
    match /{document=**} 
    {
      allow read;
      allow write: if (request.auth != null)
    }
  }
}
```