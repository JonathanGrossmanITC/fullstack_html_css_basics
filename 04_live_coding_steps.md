# Live Coding and Additional Resources

This document contains steps and code for the live lectures. In the live lectures, you watch and help a developer build a responsive web page. The main purposes of the live coding session are to refresh the HTML and CSS basics, highlight key concepts from the written materials that accompany the lecture, and show you one example of how to build a landing page from scratch. 

To help pack more content into less time so that you can see a project-based approach to writing HTML and CSS, we prepared the code for the live coding sessions in advance in order to reduce the amount of "trial and error" required when writing live HTML and CSS. This way, we can focus more on process and concepts than typing and fixing bugs. 

Hopefully some extra time permits so that the class can do some improv live coding at the end in order to simulate a more realistic beginning experience for writing HTML and CSS. We can run into bugs, get unexpected behavior that defies logic, and more. This will be good for developing problem-solving skills.   

After these sessions, you will have:  
- Refreshed basic HTML and CSS topics  
- Focused on several key concepts for layout and design  
- Seen how one developer's process for writing HTML and CSS to build a responsive landing page  

## Day 1

The focus of this live coding session is to create a project folder, design the mobile layout and styles, and add media queries to handle some of the styles for larger screen sizes. By the end of this session, the page should look fairly good but have some imperfections. For instance, the title is not propertly aligned, the footer layout is awkward in larger screen sizes, and more. In the next live coding session, you will implement styles in your media questions that address those imperfections.  

Live Coding Steps:  

1. Create a project folder for HTML and CSS  
  
2. In the HTML file, create the HTML structure for your page:  
  -- In the body, add two `div` elements. One is for a navbar (`class="navbar"`) and the other is for the main wrapper (`class="main-wrapper"`).  
  -- In the navbar, add three `div` elements (`class="navbar-item"`). The text for the elements should be Login, Signup, and ITC.  
  -- In the main wrapper, add two `div` elements. One is for a sidebar (`class="sidebar"`) and the other is a content wrapper (`class="content-wrapper"`).  
  -- In the sidebar, add three `div` elements (`class="sidebar-item"`). The text for the elements should be Schedule, Topics, and Squares.  
  -- In the content wrapper, add three `div` elements. One is a title wrapper (`class="title-wrapper"`), one is a section subwrapper (`class="section-subwrapper"`), and a third is a section (`class="footer"`).    
  -- In the title wrapper, add an `h1` tag (`class="title"`) with text for the title.  
  -- In the section subwrapper, add two `div` elements. One is for section one (`class="section section-one"`) and the other is for section two (`class="section section-two"`).  
  -- In sections one and two, add an `h1` tag (`class="section-title"`) with text for a title and also add a `div` to wrap items (`class="items-wrapper"`).  
  -- In the `div` elements that wraps the items, add five or six `div` elements (`class="section-item"`) and text for each item.  
  -- In the footer, add an `h1` tag (`class="title"`) with text for a title and also add a `div` element (`class="squares-wrapper"`) to wrap some squares.  
  -- In the `div` for wrapping squares, add eight `div` elements (`class="square"`), each of which will be in the shape of a square.  
  
3. In the CSS file, add styles for screen sizes below 320px:  

```css
* {
  box-sizing: border-box;
  margin: 0;
}

.navbar {
  background-color: #5876e9;
  display: block;
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  z-index: 1;
}

.navbar-item {
  background-color: aliceblue;
  border-radius: 5px;
  color: black;
  display: none;
  margin: 5px;
  padding: 10px;
  text-align: center;
}

.navbar-logo {
  background-color: #5876e9;
  border-radius: 5px;
  border: 2px dashed aliceblue;
  color: aliceblue;
  display: block;
  margin: 5px;
  padding: 10px;
  text-align: center;
}

.main-wrapper {
  /* position */
  position: relative;
  top: 100px;

  /* design */
  width: 100%;
}

.sidebar {
  display: none;
}

.content-wrapper {
  /* design */
  width: 100%;
}

.title-wrapper {
  /* design */
  background-color: aliceblue;
  border-radius: 10px;
  font-family: "Courier New", Courier, monospace;
  width: 98%;
}

.title {
  font-size: 28px;
  font-weight: 100;
}

.section {
  padding: 10px;
}

.section-subwrapper {
  /* design */
  background-color: white;
  width: 100%;
}

.section-one {
  /* design */
  background-color: whitesmoke;
  margin: 10px;
}

.section-two {
  /* design */
  background-color: lightgray;
  margin: 10px;
}

.footer {
  /* design */
  background-color: #5876e9;
  margin: 10px 0;
  padding: 10px;
}

.section-title {
  font-size: 22px;
  font-weight: 100;
}

.items-wrapper {
  font-size: 16px;
}

.section-item {
  /* design */
  border-bottom: 1px solid gray;
  font-family: "Courier New", Courier, monospace;
  margin: 10px;
  padding: 5px;
}

.square {
  /* design */
  background-color: white;
  height: 200px;
  margin: 3px;
  width: 200px;
}
```

4. In the CSS file, add styles for screen sizes above 320px:  

```css
@media only screen and (min-width: 320px) {
  /*your CSS Rules*/
  .navbar-logo {
    background-color: aliceblue;
    color: black;
  }

  .items-wrapper {
    /* design */
    font-size: 20px;
  }

  .square {
    /* design */
    height: 60px;
    width: 60px;
  }
}
```

5. In the CSS file, add styles for screen sizes above 640px: 

```css
@media only screen and (min-width: 640px) {
  /*your CSS Rules*/

  .navbar-item {
    display: block;
  }

  .navbar-logo {
    display: none;
  }

  .sidebar {
    /* design */
    background-color: white;
    border-right: 1px solid #5876e9;
    border-top: 1px solid #5876e9;
    margin: 0 10px 0 0;
    padding: 5px;
    width: 180px;
  }

  .sidebar-item {
    font-size: 24px;
    margin: 20px 0;
    padding: 5px;
  }

  .section-one {
    /* design */
    margin: 10px 5px 10px 10px;
  }

  .section-two {
    /* design */
    margin: 10px 10px 10px 5px;
  }

  .items-wrapper {
    /* design */
    font-size: 24px;
  }

  .square {
    /* design */
    height: 110px;
    width: 110px;
  }
}
```

6. In the CSS file, add styles for screen sizes above 960px: 

```css
@media only screen and (min-width: 960px) {
  /*your CSS Rules*/
  .sidebar-item {
    font-size: 30px;
    margin: 30px 0;
    padding: 5px;
  }

  .section {
    width: 100%;
  }

  .square {
    /* design */
    height: 150px;
    width: 150px;
  }
}
```

## Day 2

The focus of this live coding session is to use Flexbox to improve the responsive layout and design of the page. By the end of this session, most of the imperfections should be eliminated.     

Live Coding Steps:  

1. In the CSS file, revise the styles for screen sizes below 320px:  

```css
* {
  box-sizing: border-box;
  margin: 0;
}

.navbar {
  background-color: #5876e9;
  display: block;
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  z-index: 1;
}

.navbar-item {
  background-color: aliceblue;
  border-radius: 5px;
  color: black;
  display: none;
  margin: 5px;
  padding: 10px;
  text-align: center;
}

.navbar-logo {
  background-color: #5876e9;
  border-radius: 5px;
  border: 2px dashed aliceblue;
  color: aliceblue;
  display: block;
  margin: 5px;
  padding: 10px;
  text-align: center;
}

.main-wrapper {
  /* flex */
  display: flex;

  /* position */
  position: relative;
  top: 100px;

  /* design */
  width: 100%;
}

.sidebar {
  display: none;
}

.content-wrapper {
  /* flex */
  align-items: center;
  display: flex;
  flex-direction: column;

  /* design */
  width: 100%;
}

.title-wrapper {
  /* flex */
  align-items: center;
  display: flex;
  justify-content: center;

  /* design */
  background-color: aliceblue;
  border-radius: 10px;
  font-family: "Courier New", Courier, monospace;
  width: 98%;
}

.title {
  font-size: 28px;
  font-weight: 100;
}

.section {
  padding: 10px;
}

.section-subwrapper {
  /* flex */
  display: flex;
  flex-direction: column;

  /* design */
  background-color: white;
  width: 100%;
}

.section-one {
  /* flex */

  /* design */
  background-color: whitesmoke;
  margin: 10px;
}

.section-two {
  /* flex */

  /* design */
  background-color: lightgray;
  margin: 10px;
}

.footer {
  /* flex */

  /* design */
  background-color: #5876e9;
  margin: 10px 0;
  padding: 10px;
  width: 98%;
}

.section-title {
  font-size: 22px;
  font-weight: 100;
}

.items-wrapper {
  /* flex */
  display: flex;
  flex-direction: column;
}

.section-item {
  /* design */
  border-bottom: 1px solid gray;
  font-family: "Courier New", Courier, monospace;
  margin: 10px;
  padding: 5px;
}

.squares-wrapper {
  /* flex */
  align-items: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.square {
  /* design */
  background-color: white;
  height: 200px;
  margin: 3px;
  width: 200px;
}
```

2. In the CSS file, revise the styles for screen sizes above 320px:  

```css
@media only screen and (min-width: 320px) {
  /*your CSS Rules*/
  .navbar-logo {
    background-color: aliceblue;
    color: black;
  }

  .items-wrapper {
    /* flex */
    flex-direction: row;
    flex-wrap: wrap;

    /* design */
    font-size: 20px;
  }

  .squares-wrapper {
    /* flex */
    flex-wrap: wrap;
    flex-direction: row;
    justify-content: start;
  }

  .square {
    /* design */
    height: 50px;
    width: 50px;
  }
}
```

3. In the CSS file, revise the styles for screen sizes above 640px: 

```css
@media only screen and (min-width: 640px) {
  /*your CSS Rules*/
  .navbar {
    align-items: flex-end;
    display: flex;
  }

  .navbar-item {
    display: block;
  }

  .navbar-logo {
    display: none;
  }

  .sidebar {
    /* flex */
    display: flex;
    flex-direction: column;

    /* design */
    background-color: white;
    border-right: 1px solid #5876e9;
    border-top: 1px solid #5876e9;
    margin: 0 10px 0 0;
    padding: 5px;
    width: 180px;
  }

  .sidebar-item {
    font-size: 24px;
    margin: 20px 0;
    padding: 5px;
  }

  .section-subwrapper {
    /* flex */
    flex-direction: row;
    justify-content: space-evenly;
  }

  .section-one {
    /* design */
    margin: 10px 5px 10px 10px;
  }

  .section-two {
    /* design */
    margin: 10px 10px 10px 5px;
  }

  .items-wrapper {
    /* flex */
    flex-direction: column;

    /* design */
    font-size: 24px;
  }
  .squares-wrapper {
    /* flex */
    flex-wrap: wrap;
    justify-content: end;
  }

  .square {
    /* design */
    height: 110px;
    width: 110px;
  }
}
```

4. In the CSS file, revise the styles for screen sizes above 960px: 

```css
@media only screen and (min-width: 960px) {
  /*your CSS Rules*/
  .sidebar-item {
    font-size: 30px;
    margin: 30px 0;
    padding: 5px;
  }

  .section {
    width: 100%;
  }

  .squares-wrapper {
    /* flex */
    flex-wrap: wrap;
    justify-content: center;
  }

  .square {
    /* design */
    height: 140px;
    width: 140px;
  }
}
```

## Day 3  

The focus of this live coding session is to add animations to the web page and, if time permits, continue to improve the style. By the end of this session, the web page should be complete.     

Live Coding Steps:  

1. In the HTML file, find the footer. Inside the footer, add a new class to each `square`. Make the new class names unique for each square.  

```html
<!-- Rest of HTML is omitted from this sample -->

<!-- Child Three -->
<div class="footer">
  <h1 class="title">Squares</h1>
  <div class="squares-wrapper">
    <div class="square square-1"></div>
    <div class="square square-2"></div>
    <div class="square square-3"></div>
    <div class="square square-4"></div>
    <div class="square square-5"></div>
    <div class="square square-6"></div>
    <div class="square square-7"></div>
    <div class="square square-8"></div>
   </div>
</div>
```

2. In the CSS file, add a transition animation to the `square` class.  

```css
/* Rest of CSS omitted from this sample */  

.square {
  /* design */
  background-color: white;
  height: 200px;
  margin: 3px;
  width: 200px;

  /* animation */
  transition: background-color 1s;
}
```

3. In the CSS file, add a hover effect to each of the new, unique square classes.  

```css
/* Rest of CSS omitted from this sample */  

.square-1:hover {
  background-color: red;
}
.square-2:hover {
  background-color: orange;
}
.square-3:hover {
  background-color: yellow;
}
.square-4:hover {
  background-color: green;
}
.square-5:hover {
  background-color: blue;
}
.square-6:hover {
  background-color: indigo;
}
.square-7:hover {
  background-color: violet;
}
.square-8:hover {
  background-color: black;
}
```

4.  In the HTML file, find the navbar. Below it, add a new `div` element (`class="rocket"`).  

```html
<!-- Rest of HTML is omitted from this sample -->

<div class="navbar">
  <div class="navbar-item">Login</div>
  <div class="navbar-item">Signup</div>
  <div class="navbar-logo">&lt; itc ></div>
</div>
<div class="rocket">🚀</div>
```

5. In the CSS file, position the `body` tag so that you can position the `rocket` with `position: absolute`.  

```css
/* Rest of CSS omitted from this sample */  

body {
  position: relative;
}
```

6. In the CSS file, add some initial style to the `rocket` class that positions it between the navbar and main section and sets some initial styles for design.  

```css
/* Rest of CSS omitted from this sample */  

.rocket {
  /* position */
  position: absolute;
  top: 65px;

  /* design */
  font-size: 48px;
  width: 100%;
  z-index: 10;
}
```


7. In the CSS file, above the `rocket` class, add a `@keyframe` definition for the animation.  

```css
@keyframes takeoff {
  0% {
    -moz-transform: translate(0%, 0%);
    -webkit-transform: translate(0%, 0%);
    display: block;
    transform: translate(0%, 0%);
  }
  100% {
    font-size: 24px;
    -moz-transform: translate(100%, 30%);
    -webkit-transform: translate(100%, 30%);
    transform: translate(100%, -70%);
  }
}
```

8. In the CSS file, add the animation to the `rocket` class.  

```css
.rocket {
  /* position */
  position: absolute;
  top: 65px;

  /* design */
  font-size: 48px;
  width: 100%;
  z-index: 10;

  /* animation */
  animation: takeoff 7s ease-in 0s;
}
```

9. In the CSS file, revise the `rocket` class to add values for `opacity` and `transform`.

```css
.rocket {
  /* position */
  position: absolute;
  top: 65px;
  transform: translate(100%, -70%);

  /* design */
  font-size: 48px;
  opacity: 0;
  width: 100%;
  z-index: 10;

  /* animation */
  animation: takeoff 7s ease-in 0s, hide-rocket 1s ease-out 7s;
}
```

10. In the CSS file, revise the `takeoff` keyframe to add a change in `opacity`.  

```css
@keyframes takeoff {
  0% {
    -moz-transform: translate(0%, 0%);
    -webkit-transform: translate(0%, 0%);
    display: block;
    opacity: 1;
    transform: translate(0%, 0%);
  }
  100% {
    font-size: 24px;
    -moz-transform: translate(100%, 30%);
    -webkit-transform: translate(100%, 30%);
    opacity: 0;
    transform: translate(100%, -70%);
  }
}
```


## Additional Resources  
   
### HTML and CSS

[GitHub Learning Lab: Introduction to HTML](https://lab.github.com/githubtraining/introduction-to-html) 
[Marksheet: a free HTML and CSS tutorial](https://marksheet.io/)  
[HTML and CSS Tutorial](https://github.com/cassidoo/HTML-CSS-Tutorial)  
[Code Pen](https://codepen.io/)  
[HTML and CSS Practice Project](https://www.codementor.io/html_css-projects)  
[Flexbox Froggy](https://flexboxfroggy.com/)  
[Grid Garden](https://cssgridgarden.com/)  
[Bootstrap](https://getbootstrap.com/)  

### JavaScript

[GitHub Learning Lab: JavaScript with HTML and CSS](https://lab.github.com/bitprj/javascript-with-html-and-css)  
[JavaScript Projects](https://code-projects.org/c/languages/project/jsprojects/)  
[100+ JavaScript Projects for Beginners!](https://jsbeginners.com/javascript-projects-for-beginners/)  
[JavaScript Hero Exercises](https://www.jshero.net/en/success.html)  
[Code Wars](https://www.codewars.com/)  
[Exercism](https://exercism.io/tracks/javascript)  
