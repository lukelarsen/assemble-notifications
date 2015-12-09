[Assemble]:                http://assemblecss.com
[Assemble Core]:           https://github.com/lukelarsen/assemble-core
[PostCSS z-index Order]:   https://github.com/lukelarsen/postcss-zindex-order

# Assemble Notifications
Assemble Notifications is a component of the [Assemble] CSS Framework. It will give you a solid base for notifications in your project. It has some default styles that can easily be overridden so you can add your own look.

## Requirements
Assemble Buttons requires [Assemble Core].

## Installation
npm install assemble-notifications --save-dev

## Usage
### Gulp
```js
var gulp = require('gulp');
var postcss = require('gulp-postcss');
var assembleCore = require('assemble-core');
var assembleNotifications = require('assemble-notifications');

gulp.task('css', function () {
    var processors = [
        assembleCore({
            zLayerValues: {
                'modal': 9,
                'tip': 10
            }
        }),
        assembleNotifications
    ];
    return gulp.src('./src/*.css')
        .pipe(postcss(processors))
        .pipe(gulp.dest('./dest'));
});
```

## Options
Options are set with variables. These variables are already set with their default values so they will just work out of the box. If you wish to change them just define the variable you want to change before you load the _assemble-notifications.css file. You may wish you see [Assemble Core] for more examples and directions for setting up a Assemble project.

### Design Variables

##### $notification-width
- Default: 315px;
- Type: Number
```css
$notification-width: 400px;
```

##### $notification-font-size
- Default:  0.8rem;
- Type: Number
```css
$notification-font-size: 100%;
```

##### Modal z-index
This component makes use of the [postcss-constants] plugin to set the z-index. [postcss-constants] is included with [Assemble Core] so you are good to go. This helps keep all our z-index values in one place. To get this working you will need to:
1- Create a 'constants.js' file and add this to it
```js
module.exports = {
  zindexes: {
    notification: 10
  }
};
```
2- Then in your main css file add this towards the top:
```css
~zindexes: "./constants.js";
```

Now the assemble-notification component will pull the z-index values from the constants.js file. You can add more values there and call them in your css with
```css
z-index: ~zindexes.tip;
```

##### $notification-padding
- Default: 7px 15px;
- Type: String
```css
$notification-padding: 5px 10px;
```

##### $notification-close-color
- Default: #FFF;
- Type: Color
```css
$notification-close-color: #000;
```

##### $notification-close-color-hover
- Default: #000;
- Type: Color
```css
$notification-close-color-hover: #FFF;
```

##### $notification-space-from-edge
- Default: 20px;
- Type: Number
```css
$notification-space-from-edge: 25px;
```

##### Notification Colors
You will need to set a color class by using this syntax: .notification--(name)
<br>
Then you have six options to set. None are required. They are:
- bg-color
- text-color
- title-bar-bg-color
- title-bar-text-color

###### Example
```css
.notification--success{
    bg-color: green;
    text-color: white;
    title-bar-bg-color: orange;
    title-bar-text-color: black;
}
```
Will output:
```css
.notification--success{
    background: green;
    color: white;
}
.notification--success .notification__title-bar,
.notification--success .notification__title-bar h3{
    color: black;
}
.notification--success .notification__title-bar{
    background: orange;
}
.notification--success .iconic *{
    fill: white;
}
.notification--success .notification-text{
    color: white;
}
```

### Modifier Variables

##### $notification-bottom-right
- Default: false;
- Type: Boolean
```css
$notification-bottom-right: true;
```

##### $notification-bottom-left
- Default: false;
- Type: Boolean
```css
$notification-bottom-left: true;
```

##### $notification-top-right
- Default: false;
- Type: Boolean
```css
$notification-top-right: true;
```

##### $notification-top-left
- Default: false;
- Type: Boolean
```css
$notification-top-left: true;
```
