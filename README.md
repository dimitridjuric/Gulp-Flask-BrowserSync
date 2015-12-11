# Gulp Flask BrowserSync Skeleton

This is a web app skeleton using Gulp, Flask and BrowserSync.
It is based on the Yeoman webapp contructor, a skeleton (https://github.com/pebreo/gulp-browsersync-flask) and and article on realpython.com (https://realpython.com/blog/python/the-ultimate-flask-front-end/).

The project directory is:
```
Project
|   README.md
|   package.json
|   bower.json
|   bower.rc
|   gulpfile.babel.js
+---node_modules
+---app
|   |   app.py
|   +---templates
|   |       index.html
|   |       layout.html
|   +---static
|   |   |   favocon.ico
|   |   +---styles
|   |   |   |   main.css
|   |   |   |   main.scss
|   |   +---scripts
|   |   |   |   main.js
|   |   +---images
|   |   +---bower_components
+---dist
```

### Set up

You need NPM, Python and pip.
clone the project skeleton.

cd into the project folder, then
to install Flask and other python packages:

`pip install -r requirements.txt [-f app/lib]`

(-f app/lib might be necessary if you want to have that on you server/google app engine)

`npm install` to install the node modules, see list in the packages.json file 

and finally `bower install`

Note that the folder `bower_components` is not located is the root of the project directory, but in `app/static`, this is for flask to be able to
access it. For this the bower.rc does this configuration.
```
{
  "directory": "app/static/bower_components"
}
```
Now you should be able to `gulp serve` and after a few seconds you a browser page should open with a basic page. It's using bootstrap-sass, jquery, and the page automatically reload on changes for the templates, the app.py, and the sass. The Sass get recompiled automatically on changes and the page reloads.

### Gulp tasks

`gulp styles`
recompiles the scss file into a css in the `app/static/styles` folder, autoprefixes, and makes a sourcemap.

`gulp serve` starts the flask server and browsersync watches templates and styles

`gulp html` parses build blocks in templates, optimises scripts and stylesheets and copies the optimised files in the dist folder.

`gulp images` optimises images and copies them to the dist folder. It would be cool to be able to automatically create multi-resolution images for the srcset attribute, but I haven't been able to find such task for gulp.

`gulp extras` copies the extra files to the dist folder (python files)

`gulp build` does the html, styles, fonts, and extras

`gulp serve:dist` serves the compiled version

`gulp lint` doesn't really work, need to be configured, produces a lot of errors due to the use of babel and jquery. Also need to work on the `test` task.





