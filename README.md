## Website Performance Optimization NanoDegree Project

### Getting started

#### Part 1: Running PageSpeed Insights for index.html

1. Check out the repository
2. To inspect the site on PageSpeed Insights, run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

3. Open a browser and visit localhost:8080
4. Download and install [ngrok](https://ngrok.com/) to the top-level of your project directory to make your local server accessible remotely.
Ngrok allows you to securely expose local development enviroments to the internet.
5. You can download ngrok via npm
  ``` bash
  npm install ngrok --save-dev
  ```
6. To run ngrok  
  ``` bash
  $> cd /path/to/your-project-folder
  $> ./ngrok http 8080
  ```
7. Copy the public URL ngrok gives you and try running it through PageSpeed Insights! 
8. Another aproach is to run Grunt PageSpeed
9. First you need to install grunt and grunt-cli
``` bash
npm install -g grunt-cli
npm install --save-dev grunt
```
10. Then, you need to add the Grunt plugins to the project:

``` bash 
npm install grunt-pagespeed --save-dev
npm install load-grunt-tasks --save-dev
```

I've already configured the Gruntfile.js so all you need to do is 
``` bash
$> grunt
```

### Optimizations made on index.html
* Fixed render blocking css by using media types on html to mark some CSS resources as non-render blocking.
* Marked JavaScript resources as async because they are parser blocking by default. 
* Removed inline script to fix browser delays
* Compressed images
* Minified files
* Put css inline and added internal style sheet

### Optimizations made on views/js/main.js
* Used requestAnimationFrame() because this method tells the browser that you wish to perform an animation and requests that the browser call a specified function to update an animation before the next repaint.
* Refactored function changePizzaSizes() to reduce time to resize pizzas.
* De-nested the following function declarations:
  - changeSliderLabel
  - sizeSwitcher
  - determineDx
  - changePizzaSizes
* Changed ```querySelector``` to ```getElementsById()``` and ```querySelectorAll``` to ```getElementsByClassName()```    
* Debounced onScroll event.
