## Website Optimization portfolio project

To run install the project on your machine.
To do that, either clone the repository using git, or click the download zip button on the right and unzip the file.

To view the optimized page, navigate to dist, then double-click index.html.

I have optimized index.html to achieve at least a 90 PageSpeed score. I've optimized the JavaScript in pizza.html to achieve a frame rate of 60fps when scrolling. I've also reduced the time to resize pizzas in pizza.html to less than 5 ms.

Un-minified source code is in the src file.

All the codes(.js,.css,.html) in the dist directory have been minified.



####Part 1: Optimize PageSpeed Insights score for index.html

##### Optimizations:
* Reduce the size of pizzaria.jpg to 100px width
* Inline css/style.css
* Make google-analytics script async
* Add a media query for print.css
* Use Web Font Loader to load the Google webfont asynchronously
* Use Gulp to:
* Minify CSS
* Uglify JS
* Compress jpg and png files
* Minify HTML


####Part 2: Optimize Frames per Second in pizza.html

##### Optimizations:
* Move all constants out of the for loop in updatePositions
* Move the Math.sin calculation out for the for loop in updatePositions
* Move var items = document.getElementsByClassName('mover'); to the anonymous function at the bottom of the file to stop updatePositions from re-defining items on every scroll event
* Use window.items[i].style.left = items[i].basicLeft + 100 * phase + 'px'; instead of items...
* Set number of pizzas to 36 in document.addEventListener('DOMContentLoaded', function()
* Replace "querySelector" with getElementById in document.getElementById("movingPizzas1").appendChild(elem);
* Switch to document.getElementById instead of document.querySelector in function determineDx
* Declare var phase outside the for loop on line 561 to prevent it from being created each iteration
* Declare var elem outside the loop on line 599 to prevent it being created each iteration
* Declare movingPizzas outside the for loop to prevent a DOM call on each iteration
* Change CSS for .mover: Add transform: translateZ(0); will-change: transform; transform translate3d(0,0,0);
* Replace animationReady check with updatePositions in this event listener: window.addEventListener('scroll', updatePositions);



Sources:
* https://github.com/Sarika-C/frontend-nanodegree-mobile-portfolio/blob/master/views/js/main.js
* https://discussions.udacity.com/t/p4-pizza-scrolling-rasterize-paint/30713/13
* https://github.com/uncleoptimus/udacityP4/blob/gh-pages/views/js/main.js

####Part 3: Optimize Time to Resize Pizzas in pizza.html

##### Optimizations:
* Made the following changes to changePizzaSizes:
* Move document.document.querySelectorAll(".randomPizzaContainer"); outside the for loop
* Switch to document.getElementsByClassName from document.querySelectorAll in this line of changePizzaSizes
var randomPizzas = document.getElementsByClassName("randomPizzaContainer");
* Move randomPizzas.length to a local variable so the array's length property isn't accessed on each iteration
* Change CSS for .randomPizzaContainer: Add transform: translateZ(0); and will-change: transform;

##### changes :
*suggested changes have been made after the first review and have been commented as modified after the review;


Sources:
* https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByClassName
* https://javascriptweblog.wordpress.com/2010/10/11/rethinking-javascript-for-loops/


