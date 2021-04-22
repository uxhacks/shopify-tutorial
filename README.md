# Shopify Theme Development Tutorial 2021

## Set up Shopify
- Create Shopify Account ([Free Trial](https://www.shopify.com/) or [Partner Account](https://www.shopify.com/partners))
- Create A Store
- Customize Theme
- Set up Private App
- Enable Theme Read/Write Access

## Set up Git
- Install [Git](https://git-scm.com/)
- Create Folder for Shopify Theme (Terminal)
```curl
mkdir shopify-project
cd shopify-project
```
- Create Git Repository with [Github](https://github.com)
```curl
git init
```
- [Sync Folder to Git Repository](https://docs.github.com/en/github/getting-started-with-github/managing-remote-repositories)
```curl
git remote add origin [repository url]
```
- Commit Progress
```curl
git add -A
git commit -m "initial commit"
git push origin master
```

## Set up Themekit
- Install [Themekit](http://shopify.github.io/themekit)
- Download Theme with Theme Kit (Terminal)
```terminal
theme get -p=[your-password] -s=[your-store.myshopify.com] -t=[your-theme-id]
```
- Install [Node Wrapper for Theme Kit](https://www.npmjs.com/package/@shopify/themekit)
```curl
npm install @shopify/themekit
```

## Set up Sass
- Install [Sass](https://sass-lang.com/install)
- Set up SASS Folder/File Structure

## Set up Gulp
- Install [Gulp](https://gulpjs.com/docs/en/getting-started/quick-start)
- Create [Gulpfile.js](https://github.com/uxhacks/shopify-tutorial/blob/master/gulpfile.js) File
- Write Tasks (sass, watch, clean)

```js
const gulp = require('gulp');
const themeKit = require('@shopify/themekit');
const sass = require('gulp-sass');
const clean = require('gulp-clean-css');

gulp.task('sass', function() {
    return gulp.src('scss/global.scss')
    .pipe(sass())
    .pipe(clean( { compatibility: 'ie11' }))
    .pipe(gulp.dest('assets'))
});

gulp.task('watch', function() {
    gulp.watch('scss/*.scss', gulp.series('sass'))
    themeKit.command('watch', {
        allowLive: true,
        env: 'development'
    })
});
```
- Minify CSS with [Gulp Clean](https://github.com/peter-vilja/gulp-clean)
- Add CSS file to theme.liquid inside of the head

![Liquid Stylesheet](https://github.com/uxhacks/shopify-tutorial/blob/master/tutorial/images/theme-liquid-gulpfile-js.png?raw=true "Adding Styles in Shopify Liquid")

## Customizing Your Theme
- Edit Shopify Theme Code
- [Shopify Liquid](https://shopify.dev/docs/themes/liquid/reference)
- Modifying a Section
- Creating a new Section

## VS Code Extensions
- VS Code Extensions for Shopify Development