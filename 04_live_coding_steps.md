# Live Coding and Additional Resources

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
  -- In the `div` elements that wraps items, add five or six `div` elements (`class="section-item"`) and text for each item.  
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
