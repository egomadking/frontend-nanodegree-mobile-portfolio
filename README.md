# Website Performance Optimization portfolio project

Your challenge, if you wish to accept it (and we sure hope you will), is to optimize this online portfolio for speed! In particular, optimize the critical rendering path and make this page render as quickly as possible by applying the techniques you've picked up in the [Critical Rendering Path course](https://www.udacity.com/course/ud884).

To get started, check out the repository and inspect the code.

## Section 1: Getting started

### Part 1: Optimize PageSpeed Insights score for index.html

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

1. Copy the public URL ngrok gives you and try running it through PageSpeed Insights! Optional: [More on integrating ngrok, Grunt and PageSpeed.](http://www.jamescryer.com/2014/06/12/grunt-pagespeed-and-ngrok-locally-testing/)

Profile, optimize, measure... and then lather, rinse, and repeat. Good luck!

### Part 2: Optimize Frames per Second in pizza.html

To optimize views/pizza.html, you will need to modify views/js/main.js until your frames per second rate is 60 fps or higher. You will find instructive comments in main.js.

You might find the FPS Counter/HUD Display useful in Chrome developer tools described here: [Chrome Dev Tools tips-and-tricks](https://developer.chrome.com/devtools/docs/tips-and-tricks).

## Optimization Tips and Tricks

* [Optimizing Performance](https://developers.google.com/web/fundamentals/performance/ "web performance")

* [Analyzing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp.html "analyzing crp")

* [Optimizing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path.html "optimize the crp!")
* [Avoiding Rendering Blocking CSS](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css.html "render blocking css")
* [Optimizing JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript.html "javascript")
* [Measuring with Navigation Timing](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp.html "nav timing api"). We didn't cover the Navigation Timing API in the first two lessons but it's an incredibly useful tool for automated page profiling. I highly recommend reading.
* [The fewer the downloads, the better](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads.html)
* [Reduce the size of text](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer.html)
* [Optimize images](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization.html)
* [HTTP caching](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching.html)

## Customization with Bootstrap

The portfolio was built on Twitter's [Bootstrap](http://getbootstrap.com/) framework. All custom styles are in `dist/css/portfolio.css` in the portfolio repo.

* [Bootstrap's CSS Classes](http://getbootstrap.com/css/)
* [Bootstrap's Components](http://getbootstrap.com/components/)

---

## Section 2: Student Modification to Project Code

### Initial Insight Scores (need 90/90)

* mobile: 28/100
* desktop: 30/100

#### Insights improvements

* Round 1: image optim, css media: 61, 68
* Round 2: async analyics: 61, 68?!
* Round 3: separate 480px css: 61, 68
* Round 4: all local images optim: 62, 69
* Round 5: localized preview pics: 75, 89
* Round 6: undo separate 480px css: 71, 87
* Round 7: limiting to printable latin characters- no change
* Round 8: descended all JS: no change
* Round 9: re-separated 480px css: 71, 87
* Round 10: critical path CSS inlined, external CSS linked at bottom: 71, 87 (CSS no longer listed, just the web font)
* Round 10.5: (added cloudflare CDN perf change expected approx 24hrs)
* Round 11: commented out webfont: 85, 92
* Round 11.5 changed CDN settings to 8 days cache: 91, 97
* Round 12 _.css removed unneeded semicolons: 91, 97
* Round 13 Deferred styles script for CSS: 99, 99

---

### Initial frame generation average (need 60fps)

* 13.37ms (20-24fps)

#### FPS improvements

* Round 1: reduce number of pizzas to 56: 2.98ms (29-31fps)
* Round 2: removed var scrollTop out of for() loop. Not needed to be evaluated for each iteration! : 0.19ms(51-64fps)
* Round 3: updatePositions inside requestAnimationFrame in DOMContentLoaded event listener: 0.17ms(57-63fps)
* Round 4: Nested oscillation for() loop in function then used requestAnimation frame to call: 0.15(57-63fps)

---

### Initial resize pizza avg (need <5ms)

* 64-73ms

#### Resize improvements

* Round 1 attempted to use transform: abandoned- became too messy with overlaps
* Round 2 removed measurement on each randomPizzaContainer and relied on toggle value and switch case to provide a relative value to apply to randomPizzaContainer: 2.1 - 2.4ms