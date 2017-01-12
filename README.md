# Website Performance Optimization portfolio project

## How to run the project

Download the project from the URL given below and save the files in a folder on your computer,unzip it and open index.html in Chrome to start the project.

https://github.com/SumaiyaA/mobileportfolio


## Getting started

###Part 1: Optimize PageSpeed Insights score for index.html

Some useful tips to help you get started:

1. Check out the repository
1. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

1. Open a browser and visit localhost:8080
1. Download and install [ngrok](https://ngrok.com/) to the top-level of your project directory to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ./ngrok http 8080
  ```
set the javascript to async, to prevent blocking and optimized the images using Kraken.io (https://kraken.io/web-interface), the page speed got to a score of 86.Then moved the css to inline, to prevent render blocking, got to a score of 88.Then used grunt with cssmin, uglifier and htmlmin to minify the JS, CSS and HTML, got to a score of 93.
Run mobile and desktop performance tests for your deployed site using Google PageSpeed Insights.

###Part 2: Optimize Frames per Second in pizza.html

To optimize views/pizza.html, you will need to modify views/js/main.js until your frames per second rate is 60 fps or higher.The goal is to optimize it to 60fps.
####How to test it

In the Chrome Dev Tools "Customize and control DevTools" options menu (Kebab menu icon on the top right corner of the DevTools), select "More Tools > Rendering Settings". Inside the "Rendering" option screen, select "Show FPS meter".
Now when scrolling on the Pizza page, Chrome should be able to handle 60 FPS

1.I replaced the querySelectorAll with the getElementsByClassName, which gave a dramatic improvement.
2.In updatePositions(), the function accesses the DOM with the class name 'mover' every time the user decides to scroll. The 'items' variable never changes. It only needs to access the DOM once. It is moved into the global scope for updatePositions() to use.
3.To reduce painting, I used transform and backface-visibility hidden CSS properties to have them in their own seperate layers.
4.For the eventListener 'DOMContentLoaded', used the requestAnimationFrame function.
