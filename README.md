[Assemble]:                http://assemblecss.com
[Assemble Base]:           https://github.com/lukelarsen/assemble-base
[postcss-map]:             https://github.com/pascalduez/postcss-map

# Assemble Notifications
Assemble Notifications is a component of the [Assemble] CSS Framework. It will give you a solid base for notifications in your project. It has some default styles that can easily be overridden so you can add your own look.

## Requirements
Assemble Notifications requires [Assemble Base].

## Installation
npm install assemble-notifications --save-dev

## Usage
### Gulp
```js
var gulp = require('gulp');
var postcss = require('gulp-postcss');
var assembleBase = require('assemble-base');
var assembleNotifications = require('assemble-notifications');

gulp.task('css', function () {
    var processors = [
        assembleBase,
        assembleNotifications
    ];
    return gulp.src('./src/*.css')
        .pipe(postcss(processors))
        .pipe(gulp.dest('./dest'));
});
```
Then import the _assemble-notifications.css file from your css file.
```css
@import '../node_modules/assemble-base/base';

/*
Override variables here before the Assemble Components are loaded.
*/

@import '../node_modules/assemble-notifications/assemble-notifications';
```

### HTML
```html
<div class="notification-wrapper  notification-wrapper--**location modifier**">
    <div class="notification  notification--**color modifier**">
        <div class="notification__title-bar">
            <h3 class="notification-title"><img class="iconic" data-src="../images/lock.svg"> Message Title</h3>
            <div class="notification-close-btn">
                <img class="iconic" data-src="../images/close.svg">
            </div>
        </div>
        <div class="notification-content">
            <p class="notification-text">Message Text that goes on for a while so show a large message.</p>
        </div>
    </div>
</div>
```

## Options
Options are set with variables. These variables are already set with their default values so they will just work out of the box. If you wish to change them just define the variable you want to change before you load the _assemble-notifications.css file. You may wish you see [Assemble Base] for more examples and directions for setting up a Assemble project.

### Design Variables

##### $notification-width
- Set the notification width.
- Default: 315px;
- Type: Number
```css
$notification-width: 400px;
```

##### $notification-font-size
- Set the notificaiton font size.
- Default:  0.8rem;
- Type: Number
```css
$notification-font-size: 100%;
```

##### Notification z-index
This component makes use of the [postcss-map] plugin to set the z-index. [postcss-map] is included with [Assemble Base] so you are good to go. This helps keep all our z-index values in one place. To get this working you will need to:
1- Create a 'constants.json' file and add this to it
```js
{
    "zIndexes": {
        "notification": 10
    }
}
```
2- Then in your main gulp file provide the path to the newly created constants.json in the assembeCore options.
```js
assembleCore({
    basePath: 'src/',
    maps: [ 'constants.json' ]
})
```

Now the assemble-notifications component will pull the z-index values from the constants.js file. You can add more values there and call them in your css with
```css
z-index: map(constants, zIndexes, something);
```

##### $notification-padding
- Set notification padding.
- Default: 7px 15px;
- Type: String
```css
$notification-padding: 5px 10px;
```

##### $notification-close-color
- Set the notification close color.
- Default: #FFF;
- Type: Color
```css
$notification-close-color: #000;
```

##### $notification-close-color-hover
- Set the notification close hover color.
- Default: #000;
- Type: Color
```css
$notification-close-color-hover: #FFF;
```

##### $notification-space-from-edge
- Set the space the notification will appear from the edge of the browser.
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
Usage
```html
<div class="notification-wrapper  notification-wrapper--**location modifier**">
    <div class="notification  notification--success">
        <div class="notification__title-bar">
            <h3 class="notification-title"><img class="iconic" data-src="../images/lock.svg"> Message Title</h3>
            <div class="notification-close-btn">
                <img class="iconic" data-src="../images/close.svg">
            </div>
        </div>
        <div class="notification-content">
            <p class="notification-text">Message Text that goes on for a while so show a large message.</p>
        </div>
    </div>
</div>
```


### Modifier Variables

##### $notification-bottom-right
- Turn on/off notifications in the bottom right. A class of .notification-wrapper--bottom-right will be generated if true.
- Default: false;
- Type: Boolean
```css
$notification-bottom-right: true;
```
Usage
```html
<div class="notification-wrapper  notification-wrapper--bottom-right">
    <div class="notification  notification--success">
        <div class="notification__title-bar">
            <h3 class="notification-title"><img class="iconic" data-src="../images/lock.svg"> Message Title</h3>
            <div class="notification-close-btn">
                <img class="iconic" data-src="../images/close.svg">
            </div>
        </div>
        <div class="notification-content">
            <p class="notification-text">Message Text that goes on for a while so show a large message.</p>
        </div>
    </div>
</div>
```

##### $notification-bottom-left
- Turn on/off notifications in the bottom left. A class of .notification-wrapper--bottom-left will be generated if true.
- Default: false;
- Type: Boolean
```css
$notification-bottom-left: true;
```
Usage
```html
<div class="notification-wrapper  notification-wrapper--bottom-left">
    <div class="notification  notification--success">
        <div class="notification__title-bar">
            <h3 class="notification-title"><img class="iconic" data-src="../images/lock.svg"> Message Title</h3>
            <div class="notification-close-btn">
                <img class="iconic" data-src="../images/close.svg">
            </div>
        </div>
        <div class="notification-content">
            <p class="notification-text">Message Text that goes on for a while so show a large message.</p>
        </div>
    </div>
</div>
```

##### $notification-top-right
- Turn on/off notifications in the top right. A class of .notification-wrapper--top-right will be generated if true.
- Default: false;
- Type: Boolean
```css
$notification-top-right: true;
```
Usage
```html
<div class="notification-wrapper  notification-wrapper--top-right">
    <div class="notification  notification--success">
        <div class="notification__title-bar">
            <h3 class="notification-title"><img class="iconic" data-src="../images/lock.svg"> Message Title</h3>
            <div class="notification-close-btn">
                <img class="iconic" data-src="../images/close.svg">
            </div>
        </div>
        <div class="notification-content">
            <p class="notification-text">Message Text that goes on for a while so show a large message.</p>
        </div>
    </div>
</div>
```

##### $notification-top-left
- Turn on/off notifications in the top left. A class of .notification-wrapper--top-left will be generated if true.
- Default: false;
- Type: Boolean
```css
$notification-top-left: true;
```
Usage
```html
<div class="notification-wrapper  notification-wrapper--top-left">
    <div class="notification  notification--success">
        <div class="notification__title-bar">
            <h3 class="notification-title"><img class="iconic" data-src="../images/lock.svg"> Message Title</h3>
            <div class="notification-close-btn">
                <img class="iconic" data-src="../images/close.svg">
            </div>
        </div>
        <div class="notification-content">
            <p class="notification-text">Message Text that goes on for a while so show a large message.</p>
        </div>
    </div>
</div>
```
