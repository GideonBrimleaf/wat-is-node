# WAT IS NODE!?
A starter app using ExpressJS and Tailwind CSS

## Dependencies

* Node.js ~10.16.2
* npm ~6.9.0
* PostCSS ~7.1.0

## How to get an Express.js app set up

As per the [Express JS docs](https://expressjs.com/en/starter/generator.html)
you can get started quickly with the following (passing in whichever view format
you would like for your app - EJS here is the example). This will create the 
directory for your app as well as the required subdirectories

```
$ npx express-generator my-awesome-app --view=ejs
```

## How to get Tailwind CSS installed

[Surf Code Repeat](https://surfcoderepeat.com/express-tailwind) has a great blog
on this but I've made a few tweaks:

```
$ cd my-awesome-app
$ npm install tailwindcss
$ npx tailwind init
```

This will create a tailwind.config.js file in your route.  You need to rename this
to tailwind.js. You may also need to run `npm update` to ensure that your package-lock.json
file is updated to include the dependencies for Tailwind.

## Setup PostCSS for Tailwind

In the root of your directory

```
$ touch postcss.config.js
```

Open up the newly created file and fill it with the following

```
const tailwindcss = require('tailwindcss')

module.exports = {
  "plugins": [
    require('tailwindcss')('tailwind.js'),
    require('autoprefixer')(),
  ]
}
```

## Create a Tailwind CSS file in your project

This file can be called whatever you like but be sure to adjust the later
commands to refer to the name of your css file:

```
$ touch public/stylesheets/tailwind.css
```

Open up the file and as per the [Tailwind docs](https://tailwindcss.com/docs/installation)
add the following:

```
@tailwind base;
@tailwind components;
@tailwind utilities;
```


## Add a script to the package.json file

There will already be a script in your package.json file so the following should
replace all of the exisitng entry:

```
"scripts": {
    "start": "npm run build:css && node ./bin/www",
    "build:css": "postcss public/stylesheets/tailwind.css -o public/stylesheets/style.css"
  }
```

Finally - kick it all off:

```
DEBUG=my-awesome-app:* npm start
```

And you'll have your own express app with Tailwind ready to go!
