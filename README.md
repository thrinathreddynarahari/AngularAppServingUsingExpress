# Deploying Angular Application in Heroku.

Hi Dev , To deploy an angular app in Heroku follow the below procedure.

-----

## Create a new Angular project.

```
ng new exampleDeployDemo
```
-----

## Install express and path packages.


```
npm install express path --save
```

-----

## Create a file in project level with name 'server.js' and add the following code in that file.

```
const express = require('express');
const path = require('path');

const app = express();


app.use(express.static('./dist/angular-demo-deploy'));               // Change this to name of the build folder in dist folder
app.get('/*', (req, res) =>
    res.sendFile('index.html', {root: 'dist/angular-demo-deploy/'}), // Change this to name of the build folder in dist folder
);

app.listen(process.env.PORT || 8000);
```

-----

## Add the following command in the 'package.json' file under the 'scripts'.

```
"heroku-postbuild": "ng build"
```
-----
## Add the node and npm engines.

```
"engines": {
    "node": "14.18.2",
    "npm": "6.14.15"
  }
```
-----

## Change the start command as below.

```
"start": "node server.js"   
```


-----

### After completion of adding the above in 'package.json' your 'package.json' should look something like this.

![This is an image](https://raw.githubusercontent.com/thrinathreddynarahari/AngularAppServingUsingExpress/main/pakageJsonHerokuAngularDeployment.png)

-----
## Run the following command to Serve the angular app on express server.

```
npm run start
```
                            
### Open the configured port in browser.

Congrats! You have deployed angular app using express.
-----
