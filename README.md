# Grunt project base

A handy basis for front end JavaScript projects built with Node and Grunt.

Preconfigured to run JSHint analysis and Jasmine unit tests (with code coverage stats) before concatenating and minifying files. Also comes with Travis CI and Coveralls preconfigured.

## Setup

Make sure Node and the Grunt CLI are both installed.
- Node: https://nodejs.org/
- Grunt CLI: with Node installed, run `npm install -g grunt-cli`

Then:

0. Fork this repo.

0. Update package.json to include your project and author details

0. run npm install to get the configured Grunt packages.

As your project progresses, you'll probably need to update many of the tasks' configurations in `gruntfile.js` to account for your project's dependencies, and to update code coverage thresholds to keep code quality high.

## Processes included

- grunt-contrib-less (building of Less to CSS)
- grunt-contrib-jshint (JS static analysis)
- grunt-contrib-jasmine (JS unit testing)
- grunt-template-jasmine-istanbul (JS code coverage analysis)
- grunt-coveralls (JS code coverage reporting)
- grunt-contrib-concat (concatentaion of JS and CSS)
- grunt-contrib-uglify (minification of JS)
- grunt-processhtml (processing of HTML)
- grunt-real-favicon (generation and referencing for favicons)
- grunt-contrib-copy (copying of static files)
- grunt-contrib-watch (watching and processing of project files)
- http-server (local hosting and live updating of project files)

## Useful processes and tasks

#### live-server

Run this process from the *src* directory to locally host the dev version of your project, or from the root project directory to host the built version. Any changes to the hosted files will cause the relevant browser tab to refresh.

#### grunt watch

Begins watching `gruntfile.js`, all .less files in the *src/less/* directory and all .js files in the *src/js/* and *test/* directories. When any of them change, the .less files will be built to *css/styles.css* and JSHint will run on the .js files, then any Jasmine specs in the *test/* directory will run. JSHint and Jasmine results will be output to the console each time.

#### grunt build

Runs JSHint and Jasmine (with code coverage) on the .js files, builds .less files to styles.css, then concatenates and uglifies the .js and .css files. It then runs processhtml on *src/index.html*, and finally uses *src/example.png* as a basis for creating cross-platform favicons and adds references to *index.html*.

Build files are output to a directory named *dist/*, with the exception of *index.html* which is output to the root project directory. This makes it easy to publish project to GitHub Pages.

#### grunt test

Runs the JavaScript-related portions of `grunt watch`.

#### grunt less

Runs the Less-related portions of `grunt watch`.

#### grunt travis

Intended only for use within Travis CI. Identical to `grunt test`, but calls out to Coveralls to analyse code coverage.
