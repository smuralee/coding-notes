# Custom theme in Angular Framework

Angular applications being built by individuals often need custom look and feel. Layout theme becomes an important aspect of for the user interface. For incorporating a custom theme in Angular, we will be using [Angular Material](https://material.angular.io)

Let's start with a simple Angular application using [Angular CLI](https://github.com/angular/angular-cli)

Below are the commands to create a sample application.

```shell
# Install Angular CLI
npm install -g @angular/cli

# Create an app and incorporate Angular Material support. Include animations and gesture, if needed
ng new angular-app
npm install --save @angular/material
npm install --save @angular/animations
npm install --save hammerjs
```


Once available, we need to modify the default stylesheet to be `scss` instead of `css`. below command will modify the .angular-cli.json to use `scss` as the default stylesheet.

```shell
cd angular-app
ng set defaults.styleExt scss

# Run the npm install to download all dependencies
npm install
```
Once the stylesheet is changed, rename `styles.css` to `styles.scss` in the `src` folder. Now within the `/src/assets` folder, create a new folder `css` and add a custom theme file, `app.theme.scss`

```scss
@import '~@angular/material/theming';
// Plus imports for other components in your app.

// Include the common styles for Angular Material. We include this here so that you only
// have to load a single css file for Angular Material in your app.
// Be sure that you only ever include this mixin once!
@include mat-core();

// Custom palette definition
$mat-app-blue: (
  50 : #e2eaf2,
  100 : #b6cbdf,
  200 : #85a9ca,
  300 : #5487b4,
  400 : #306da4,
  500 : #0b5394,
  600 : #0a4c8c,
  700 : #084281,
  800 : #063977,
  900 : #032965,
  A100 : #95b6ff,
  A200 : #6294ff,
  A400 : #2f71ff,
  A700 : #155fff,
  contrast: (
    50 : #000000,
    100 : #000000,
    200 : #000000,
    300 : #ffffff,
    400 : #ffffff,
    500 : #ffffff,
    600 : #ffffff,
    700 : #ffffff,
    800 : #ffffff,
    900 : #ffffff,
    A100 : #000000,
    A200 : #000000,
    A400 : #ffffff,
    A700 : #ffffff,
  )
);

$mat-app-green: (
  50 : #e7efe4,
  100 : #c3d6bb,
  200 : #9cbb8e,
  300 : #749f61,
  400 : #568b3f,
  500 : #38761d,
  600 : #326e1a,
  700 : #2b6315,
  800 : #245911,
  900 : #17460a,
  A100 : #94ff7d,
  A200 : #6aff4a,
  A400 : #40ff17,
  A700 : #2dfc00,
  contrast: (
    50 : #000000,
    100 : #000000,
    200 : #000000,
    300 : #000000,
    400 : #ffffff,
    500 : #ffffff,
    600 : #ffffff,
    700 : #ffffff,
    800 : #ffffff,
    900 : #ffffff,
    A100 : #000000,
    A200 : #000000,
    A400 : #000000,
    A700 : #000000,
  )
);

$app-primary: mat-palette($mat-app-blue, 800, A100, A400);
$app-accent: mat-palette($mat-app-green, 800, A100, A400);

// The warn palette is optional (defaults to red).
$app-warn: mat-palette($mat-red);

// Create the theme object (a Sass map containing all of the palettes).
$app-theme: mat-light-theme($app-primary, $app-accent, $app-warn);

// Include theme styles for core and each component used in your app.
// Alternatively, you can import and @include the theme mixins for each component
// that you are using.
@include angular-material-theme($app-theme);
```

The new palette of primary and accent colours will be the default theme of the application. Now import the theme into the `styles.scss`.
 
```scss
@import "assets/css/app.theme";
```
 

We can add all the custom colour schemes into the theme and refer in the application. 
 
