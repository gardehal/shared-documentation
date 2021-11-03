# Kotlin Heroku

Heroku is a cloud based platform provider which supports many popular languages and third party softwares that you can deploy in the same Linux container (caleld "Dynos") as your program. In addition to this, it has a free-tier with a reasonable limitations for personal projects.

- [Herokus pricing tiers](https://www.heroku.com/pricing)
- [Heroku app dashboard](https://dashboard.heroku.com/apps)

## Heroku CLI

Herokus CLI is a useful tool for managing apps without using the heroku GUI. It offers the same functionality as the GUI.

1. [Download and install Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)
1. Login
    - $ `heroku login`

- [List of Heroku CLI commands](https://devcenter.heroku.com/articles/heroku-cli-commands)

## Create an app

Apps can be created with or without a Heroku Git. The Git is needed for deploment with Heroku Git and for third party packages that can be used with heroku-buildpack-apt.

#### CLI

> :information_source: **Requires Heroku CLI.**

- With Heroku Git
    - $ `heroku create`
- Without Heroku Git
    - $ `heroku create --no-remote` 

#### GUI

1. Go to [your dashboard](https://dashboard.heroku.com/apps)
1. Click the "New" button, top right, and select "Create new app"
1. Enter the name of the app, which has to be unique on Heroku
1. Chose your region
1. Click "Create app"

## Deployment

There are multiple ways to deploy an app, though doing so through Git or CLI are (probably) the most common ways.

> :information_source: **Regardless of  which way you deploy your app, you must add a buildpack for Java.**

This can be enabled though Heroku CLI:
1. Add the JVM buildpack
    - $ `heroku buildpacks:add heroku/jvm -a [app-name]`

... or in the the GUI:
1. Go to your apps settings
    - https://dashboard.heroku.com/apps/[app-name]/settings
1. In the "Buidlpacks" section, click "Add buildpack"
1. Enter this URL in the field: `https://github.com/heroku/heroku-buildpack-apt`
1. Click "Save changes"

Additionally:
1. Set up your [Procfile](https://devcenter.heroku.com/articles/procfile)
    - Heroku will use this file to initiate your code.
    - E.g.: `web: java -jar MyProgram.jar` for a web-process.
1. Set up your [App.json file](https://devcenter.heroku.com/articles/app-json-schema)
    - This contains information describing your app
    - It can be as simple as `{ "name": "[app-name]" }` 

> :information_source: **This section assumes you have an executable .jar-file of your Kotlin program.**

#### CLI

> :information_source: **Requires Heroku CLI.**

##### TODO check on requirements of core files

1. Deploy the [jar-name].jar to your [app-name] app, this does not reqquire a Heroku Git or a GitHub link, only the .jar-file
   - $ `heroku deploy:jar [jar-name].jar --app [app-name]`

#### Heroku Git, using CLI

> :information_source: **Requires Heroku CLI.**

1. Push the core files (App.json, Aptfile, Procfile, .jar-file) or just all the files to the Heroku Git master branch
    1. $ `git add .` (all files)
    1. $ `git commit -m "First deploy"`
    1. $ `git push heroku master`
1. Assuming your process "web" in the Procfile, start the app with the CLI
   - $ `heroku ps:scale web=1`

#### Integration with GitHub

Heroku can fetch updates from your GitHub repository, but you have to connect it first.

1. Go to your apps deploy-tab
    - https://dashboard.heroku.com/apps/[app-name]/deploy/heroku-git
1. Go to your Heroku app.
1. In the deploy-tab, click "GitHub" in the "Deployment method" seciton
1. New users may have to connect and approve the GitHub and Heroku accounts.
    1. Click "Connect to GitHub" in the "Connect to GitHub" section
    1. Finish the OAuth connection if it doesn't connect automatically.
    - To disconnect GitHub from Heroku, go to your [GitHub account](https://github.com/settings/applications) and reove access to Heroku. You may have to reconnect to other apps if you have any.
1. In the "Connect to GitHub" section, chose the account you wish to connect to and search for the repository. 
1. Click "Search"
1. You can chose which brantch to deploy from, using the "Automatic deploys" that appears when you successfully connect to a repository, or manually deploy from the "Manual deploy" section.
