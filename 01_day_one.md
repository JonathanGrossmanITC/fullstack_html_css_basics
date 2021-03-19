# Day 1: HTML and CSS Basics

HTML, CSS, and JavaScript are the three main languages required for building the frontend of a web application. HTML and CSS are used primarily to organize and style the contents of a webpage. In contrast, JavaScript is used to provide functionality to your page. For instance, using JavaScript, you can send the values entered into a form to a server or change the information shown on the page based on what the user clicks.  

Read this lesson and look at the links before the first class. In class, you will be expected to be familiar with the topics in this document. You will watch a live coding session that uses the concepts discussed in here. In that live coding session, we will set up our frontend web application and begin building our mobile-first design.  

We will start the class by building the folders and files the browser needs to load our web application. In doing this, we will do a quick refresher on what HTML and CSS are. We will talk about how when a user opens a browser on their computer, the browser requests the HTML, CSS, JavaScript, and media files the browser needs to build the webpage (i.e., the source code). The browser uses the source code and other files to assemble the webpage for the user to see and interact with.

Here in this lesson, you start by studying the very basics of HTML and CSS. This will help you build your project folder and connect your HTMl, CSS, and JavaScript files. Next, you'll learn about using external stylesheets and CSS selectors. Then, you'll learn about a mobile-first approach to web development. This mobile-first approach will help you think about how to approach structuring your code as your start your project.  

Although this lesson assumes you already have some HTML, CSS, and JavaScript skills, it is not required that you do.

By the end of this lesson, you will have:

- A refresher on [HTML and CSS basics](#html-and-css-refresher) and a good idea of how to structure your project folder    
- An intro to [CSS Selectors](#css-selectors) and the ability to work with an external stylesheet    
- Mobile-first design using [media queries](#media-queries) to help you think about structuring your project from the start    
- Self-study resources for learning about pseudo elements  

## [HTML and CSS Refresher](#html-and-css-refresher)

HTML and CSS are languages that instruct the browser how to display the contents on the page. HTML defines the **elements** of the page. The elements of the page consist of text, images, videos, content blocks, and more. HTML and CSS together define the **layout** and **style** of the elements. The layout is how the elements are organized on the page. The element styles include the size, spacing, color, font, and more.  

### A webpage is a document
You're probably familiar with working in a Word Doc, Google Doc, Notepad, and .txt files. Similar to those, and HTML file is just a document for storing information. Try this. Make a file on your desktop called `document.html`. Open it and write the sentence "This is just a document". Save the file. Open a browser and drag your `document.html` file to the brower. What do you see in the browser?  

Pretty cool, but wouldn't it be better if you could add some style to the text? You could change its color, position, size, and more. Using HTML and CSS syntax, you can tell the browser how to do those things. That's one of the things that makes HTML and CSS so special is that browsers know how to interpret those kinds of files and display them to the user.  

In this section, you'll learn about HTML tag syntax. This is a special syntax you need to use so that the browser knows what to do. Before studying the tag syntax, first, you'll see an example of how to structure an HTML page. In order to maximize the use of an HTML file, you need to know how to structure one. Then, you'll study some different tag types and how they work.   

Before going further, here is an example of a basic HTML document structure, which the browser reads from top to bottom:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Hello</title>
  </head>
  <body>
    <h1>Hello ITC!</h1>
    <h2>Welcome.</h2>
    <p>This is text inside a paragraph tag.</p>
    <div>This is text inside a div.</div>
    <h4>
      <span>This half is in a span, </span>
      <span>and this half is in a different span.</span>
    </h4>
  </body>
</html>
```

The example above uses multiple HTML tags. At the top, the `<!DOCTYPE html>` tells the browser that this file is an HTML file. Next, the `html` tag is the main element that wraps all the other HTML tags. The `head` tag holds meta data about the page. Here, the meta data in the `head` tags sets the title that you see in the browser's tab at the top. Look for it in the image of the example below. Other meta data, however, is usually just for the browser to read, not for the user to see. An example is a link to a stylesheet, which you'll see below in the CSS section.  

The `body` tag holds all the content for the page. It wraps all the page's content-holding elements and indicates to the browser that this is where the content is located.  

Inside the body are the content-holding tags. In this example, the content is text. You see `h1`, `h2`, and `h4` tags, each of which come with different default font styling. You also see `p`, `div`, and `span` tags, each of which comes with its own default styling. More on this later. The bottom line is that inside the `body` element is where you'll put the content that the user sees in the browser.  

To see this HTML in your own broswer, download this repository and drag to the browser the [hello html file](html/hello.html). It should look like this:

![](images/hello_html_photo.png). 

Finding [HTML examples](https://www.w3schools.com/html/html_examples.asp) online is a great way to help you write your own code.  

As the example demonstrates, a website is really just a document. You can display the document either in the browser window or as the HTML source. When viewed in the browser, you see the page content organized and styled for the end user. When viewed as source code, you see all the HTML code. Regardless, it is the same document.  

The webpage document relies upon other documents for content, style, and functionality. The HTML document relies upon CSS documents, images, and other files for conetent and style. It relies upon JavaScript files for functionality.  

In your project folder, organize your files similar to the structure here in this repository.

```html
-root
  --css
    ---styles.css
  --js
    ---index.js
  --html
    ---about.html
  --images
    ---image.png
  index.html
```

The root folder contains subfolders for `css`, `js`,`html`, and `images`. Usually, you put the `index.html` in the root folder. You can name the root folder whatever you want, like `portfolio_project` or whatever.


### Developer Tools

When you start practicing JavaScript, you will learn about the Document Object Model (DOM). The DOM is a JavaScript object that represents the HTML document. When in the form of a JavaScript object, you can write JavaScript code that interacts with your HTML file through this JavaScript object. This is how you add functionality to HTML documents.  

To help interact with the DOM, HTML syntax uses tags to define elements in which you can put content. Every element in an HTML document is stored in the DOM. Using a scripting language like JavaScript, you can access and manipulate each element on the DOM.

To help visualize the DOM and develop your code, you can use the inspector in your browser. Here is an example:

![](images/inspector.png)

As you see in the example, for any website you can right click on any part of the screen, and click **"Inspect"** in the popup menu. The developer tools will open, in which you find the **Elements** tab. Inside that tab, you can see a visual representation of your DOM object based on your HTML document's source code. Specifically, among other things, you can see the HTML and CSS of the document. You can even modify the DOM right here in your Elements tab. For instance, you can change the style properties or the text. When modifying the code in the Elements tab, you're only modifying it for that browswer session. It's not saving your modifications to your HTML file. Simply refreshing the browser will revert the webpage back to pre-modification. This is, however, a common way to test your changes before actually making those changes in your code.  

Note that the browser source code is public. When you load a webpage, the files on which the browser loads the page are accessible in the developer tools. Look at the **Sources** and **Network** tabs. What do you see? Because frontend files are public, when using private information in your code, like access tokens and passwords, you should not put them in your frontend source code. You learn more about this later in the course.

As a developer, you oftentimes use the Elements tab in the inspector to better understand how your HTML is organized, to debug CSS issues, and to try out new styles before writing your code. When you start writing JavaScript and server-side code, you use the inspector for much more, too.

### Tag Boundaries

All HTML tags have boundaries -- a beginning and an end. Many HTML tags declare their beginning and end using an opening tag *and* a closing tag. The opening tag starts with `<` and ends with `>`, like this `<div>`. The closing tag starts with `</` and ends with `>` and the text between must match the same in the opening tag, like this `</div>`. The difference between opening and closing is the `/` that is absent in the opening but present in the closing tag. Between the opening and closing tags appears other HTML elements or text. Here is an example:

```html
<div>This is some text in a div element.</div>
```

In the example above, you have opening and closing `div` tags with text between. The webpage will display the text but not the `div` tags. Rather, the browser uses the `div` tags to format and style the page _behind the scenes_.

Although many elements require both opening and closing tags, some elements define their boundaries using a self-closing tag. A self-closing tag consists of only one tag, which both opens and closes the element. A self-closing tag starts with `<` and ends with `/>`, like this `<img />`. The content is declared as an **attribute** of the tag. Here is an example:

```html
<img src="./images/image.jpg" />
```

In the example above, you have a self-closing `img` tag that sets its source attribute (`src`) as `./images/image.jpg`, which means it is showing `image.jpg` as its content on the webpage. In the browser, you will see the image but not the `img` tag. Instead, the `img` tag tells the browser that this is an image.   

### Attributes

As you can see from the `img` tag example, HTML tags can also have **attributes**. An attribute is a property of the tag. For instance, the `img` tag's `src` attribute declares which image to display. Another example is the tag used for making links -- the `a` tag. The `a` tag has an `href` attribute, which is what you need to set to tell the link where to go when clicked. Here is an example:

```html
<a href="https://facebook.com">facebook</a>
```

In the example, the `a` tag's `href` attribute is set to `"https://facebook.com"`, which means that when the link is clicked, the browser will direct the user to `https://facebook.com`.

Not every HTML tag has the same set of attributes. To help you know which tags have which attributes, here is a [list of attributes and their corresponding tags](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes).

### Default Style

In addition to boundaries and attributes, many HTML tags each have their own **default style properties**. For instance, the `div` tag has a default `display` property set to `block`. The defining characteristic of the `block` display property is that, unless overridden by other styles, it does not allow other HTML elements next to it. In other words, the preceding element in your code will appear above it in the browser and the next element in the code will appear below it in the browser. The `block` element takes up the entire line. Other tags with `display: block` are the `h1` - `h6` tags.  

In contrast, the `span` tag has no default `display` property, which makes its `display` property default to `inline`. Other tags also have no default `display` property (`display: inline`), like the `img` and `a` tags. The defining characteristic of the `inline` display property is that, unless overridden by other styles, it allows other HTML elements next to it. In other words, the preceding element in the code can appear to the left of it in the browser and the next element in the code can appear to the right of it in the browser. Of course, where those elements actually appear will also depend upon the other display properties of the `inline` element and the display properties of the neighboring elements.

Although the preceding examples focus on built-in `display` properties, HTML tags can have other default style properties. For instance, the `h1` - `h6` tags each have their own unique default `font-size`. The `a` has a built-in `text-decoration` property set to `underline`. Here is a [list of HTML elements](https://www.w3schools.com/TAGS/default.ASP). Click on each one to learn about its default style properties. 

As demonstrated above, some of the content-holidng HTML tags you should pay special attention are `div` (a generic tag that holds other tags, used for structuring sections, blocks, etc), `h1`- `h6` (hold text and present it as header text), `p` (holds text and presents it as a paragraph), `img` (presents an image), and `a` (an anchor tag, which creates links and it holds text).

Although HTML tags come with some default style properties, most often you won't rely solely upon the built-in styles for organizing and styling your webpages. Rather, you will write your own CSS styles that either supplement or override the default styles that come with each HTML tag. Therefore, aside from special cases like the `html`, `head`, and `body` tags, you need to _not_ put too much emphasis on choosing the _perfect_ HTML tag for each situation. Rather, just know that each HTML element has built-in styling that may serve you in different situations and that you can override whatever styles come with the tag.

### CSS Styling

Cascading Style Sheets (CSS) is the language used for defining the organization and style of the content-holding elements in an HTML document. You can add CSS to your HTML tags by writing your own CSS or using a CSS framework.

When writing your own CSS, it is oftentimes best to use an **external stylesheet**. This is when you write your CSS inside a CSS file and import that file into your HTML file. Writing your CSS in a CSS file instead of your HTML file will lead to cleaner, more reusable, and more efficient code.

Other approaches for writing your own CSS exist too, like writing your CSS inside a `script` tag nested in the `head` tag. You also can write the CSS in the HTML tags themselves using the `style` attribute. You will see examples of these two approaches out in the wild. Regardless of whichever approach you use, it is a good practice to be consistent in your code. That way someone else (or the future you) doesn't have to look in too many places to find where the style properties are defined for a specific element. That becomes hard if styles are not located in predictable places. So, try not to mix different patterns for styling your app.

Here, you will see an example using an external `.css` file and an example using the `style` attribute. Remember, however that the external `.css` approach is best.  

When using a CSS framework, you will import the framework into your HTML file and then use the framework's documentation to know the proper syntax for how to style your elements. You will have an introduction to the Bootstrap CSS framework in another lesson.  

### CSS File  

When writing your own CSS in an external file, you first should create in your project's root folder a subfolder names `css`. Inside that subfolder, create a stylesheet file, which is a file ending in `.css`. Typically, for your main HTML page, you should name the stylesheet `styles.css` because that's the convention. However, you can name it whatever you want.

Inside your HTML file, you need to import the stylesheet. Do this in the `head` tag using a `link` tag.

```html
<head>
  <link rel="stylesheet" href="../css/styles.css" />
</head>
```

In the code above, the `head` tag wraps the `link` tag. The `link` tag has two attributes, `rel` and `href`. The `rel` attribute creates a relationship between the HTML file and the `href` of the `link` tag. The `href` of the link tag, here, is the relative pathname of the stylesheet. In the `href`, the `..` tells the browser to look not in the current folder, but the folder that the current folder lives in; the `css` means that once it is in the folder holding the current folder, it should look for the `css` folder; the `styles.css` tells the browser which file in the `css` folder to import.  

Note that the `link` tag links documents and is used inside the `head` tag. This is different from the `a` tag, which is used inside the `body` for linking to other webpages. Although conceptually not confusing, the naming can sometimes be.  

Because the browser reads the HTML file from top to bottom, when reading the HTML file, the browser imports and reads the CSS file before reading the HTML body. This means that the CSS code that you write will essentailly be inside your HTML file, and you can use the CSS class in the `.css` file to style your HTML elements.

To test whether you properly improted the CSS file into your HTML, you should write a CSS class. When writing a CSS class that applies to all elements of a certain tag type, first you need to declare which HTML element type it applies to, for instance, `h1`, `div`, `img`, etc.

Then should follow an object, which you declare using `{ }`. Each class object is comprised of key:value pairs separated by a semi-colon. Each key is the name of a CSS property and each value defines that property for the class you're writing. Here is an example of a CSS class for the `h1` tag:

```css
h1 {
  background-color: gray;
  color: blue;
  margin: 10px;
  padding: 20px;
  width: 50%;
}
```

In the example above, the class is for `h1` tags in your HTML file and has key:value properties that set the background color, text color, margin, padding, and width. Background color, text color, and width are self-explanatory. Margin and padding maybe not. Margin is the space surrounding the element. Padding is the space inside the element between the element's boundary and the content inside it. So margin defines the space between elements and padding defines the space between the element and its own content inside.

Many other CSS properties exist. Here is a [list of CSS Properties](https://www.w3schools.com/cssref/default.asp). Use it as a resource when styling your web applications.  

To see an examplein your own browser, download this repository and drag to the browser the [styles html file](html/styles_one.html). It should look like this:

![](images/styles_one_photo.png)

### CSS Style Attribute

Instead of using a stylesheet, you can use an HTML element's `style` attribute to add CSS to your webpage. Set the `style` attribute to a string (not an object) containing key:value pairs separated by a semi-colon. Like a CSS class in an external `.css` file, each key is the name of a CSS property and each value defines that property for the class you're writing. Here is an example:

```html
<p
  style="
        background-color: aliceblue;
        color: gray;
        margin: 10px;
        padding: 20px;
        width: 50%;
      "
>
  This is text inside a paragraph tag.
</p>
```

In this example, you set the `style` attribute of a `p` tag equal to a string containing key:value properties that set the background color, text color, margin, padding, and width.

To see an example in your own browser, download this repository and drag to the browser the [styles html file](html/styles_two.html). It should look like this:

![](images/styles_two_photo.png)

You will see this approach online in tutorials and documentation, so you should know how to read it. Remember, however, that your web applications will be easier to read and maintain and lead to more efficient code if you use external stylesheets instead of the `style` attribute.

## [CSS Selectors](#css-selectors)

Use CSS selectors in your CSS stylesheets to select which HTML elements you want to style. This allows for more precision than the example above where you styled all of one tag type (i.e., the `h1` tags) and more flexibility than using the `style` attribute, like in the example above where you styled only one `p` tag. You have [many CSS selectors](https://www.w3schools.com/cssref/css_selectors.asp) available to use, and we will cover one called the _`.class`_  selector and several others in an example using a checkers board.

The _`.class`_ selector styles all elements whose `class` attribute contains the name of the _`class`_. For instance, the `.page-title` class in your CSS stylesheet will apply to all the HTML elements whose `class` attribute is equal to `"page-title"`. Here is an example of the class in your CSS file:

```css
.page-title {
  background-color: black;
  color: white;
  margin: 10px;
  padding: 20px;
  width: 50%;
}
```

Now that you have a CSS class, you should apply it to an HTML element. Using the HTML element's `class` attribute, you can match an HTML element to your CSS class name. Here is an example:

```html
<h1 class="page-title">Hello ITC!</h1>
```

In the example, you style the `h1` tag with the `.page-title` custom class you wrote by setting the `h1` tag's `class` attribute equal to the name of the CSS class as a string`"page-title"`. Instead of styling all the `h1` tags, you only styled the one with its `class` set to `.page-title`.  You can, however, apply that same `class` to multple HTML elements of any type. So it's reusable, unlike the `script` example above. Also, you can apply more than one selector to an HTML element. If in addition tothe `.page-title` selector, you also have a `.bold-text` selector, you can apply both to the same HTML element by putting a space between the class name, like this:

```html
<h1 class="page-title bold-text">Hello ITC!</h1>
```

Note, that if the `.page-title` and `.bold-text` classes were to have conflicting styles (e.g., one with `font-weight: 100` and the other with `font-weight: 900`), the one appearing lower in the `.css` file will win.  

As you can see from the example, the syntax for a _`.class`_  selector is a `.` followed by a name that you choose. When naming your own class, choose names that are unique, short, and descriptive. Good naming will make your code easier to maintain. Plus, good naming helps you tell a story with your code, which makes it easier to understand. When someone reads it, good names bring your code to life! Avoid using names that are the same as those for built-in functions and variables, other reservered names, and the same as other variables of yours.

In CSS, your class names are for objects, not actions. Therefore, it's recommended to use nouns. For instance, `.spinner`, `.success-alert`, and `.page-title` are nouns that would help explain your code. Also, use `kebab-case` when your CSS class name has multiple words.

The _`.class`_ selector is just one of many options. You have [lots of CSS selectors](https://www.w3schools.com/cssref/css_selectors.asp) available to use. For instance, selectors exist for selecting elements with more than one class, elements of only a certain type with a specific class, elements with certain text in an attribute, and more. You also can use selectors to target parts of an element, like its active link, the status of whether it's checked or not, and the space before and after the element.

Check out the [Checkers Example](html/checkers.html) in the code and in your browser to see if you can understand how it works. It's a simple example. Study the [list of CSS selectors](https://www.w3schools.com/cssref/css_selectors.asp) and think about how maybe you could add some cool features to the example.


## [Media Queries](#media-queries)  

Media queries are used in responsive web design to help customize the view based on the user's screensize. In other words, media queries allow you to set HTML element properties that depend upon whether a certain condition is true. For purposes of responsive web design, usually that contidion is the screen width. So, for instance, you can choose for an element to have `font-size: 28px` when the screen is greater than `760px` wide and `font-size: 24px` when the screen is less than or equal to `760px`. This means that you can design webpages that look great on phones, tablets, and computers of all sizes.

### Media Query Syntax and Example

This section focuses on media queries for responsive web design. You write media queries in your CSS code. The syntax for media queries requires `@media` followed by a condition, and then an object containing CSS classes. The CSS classes in the media query must be below its corresponding class in the [CSS document](https://stackoverflow.com/questions/7859336/why-are-my-css3-media-queries-not-working).  

Here is an example of a media query from a CSS file: 

```css
body {
  background-color: blue;
}

@media only screen and (max-width: 600px) {
  body {
    background-color: red;
  }
}
```

In the example above, you see the `@media` syntax followed by the condition ` only screen and (max-width: 600px)`, which translates to "only when the screen is 600px or less". This is called a breakpoint. Then comes the object containing CSS classes. Ultimately, the `body`'s background color will be `red` when the screensize is `600px` or less. Otherwise, it is` blue`. 

In your browser, look at the example [media queries file](html/media_queries.html). Change the browser size. See how below `600px` screen width the background is `red` and above it is `blue`. Now, modify the code to add other CSS styles to your breakpoint so that more than just the background color changes. Also try adding additional breakpoints. When doing so, know that the order or your [media queries matters](https://stackoverflow.com/questions/8790321/why-does-the-order-of-media-queries-matter-in-css).

For more on media queries generally, check out [W3 Schools Media Queries](https://www.w3schools.com/cssref/css3_pr_mediaquery.asp) page.

### Mobile-First Approach

When writing responsive web applications, you need to write CSS that accounts for screens of all sizes. By taking a mobile-first approach, you design your application for mobile screens and then use media queries to account for larger screens. A mobile-first approach results in a faster page display on smaller devices.

Your standard styles are those appearing outside the media queries, and your media query styles are those inside the media queries. With a mobile-first approach, your standard styles will control the style generally and on mobile devices, and the media queries will control some of the styles in larger screens. The condition in your media queries, thererfore, will change the design when the page increases in size.

Here is an example of a [set of media queries](https://stackoverflow.com/questions/28016406/problems-with-media-queries/) for mobile first:

```css
@media only screen and (min-width: 320px) {
    /*your CSS Rules*/     
}
@media only screen and (min-width: 480px) {
    /*your CSS Rules*/     
}
@media only screen and (min-width: 640px) {
    /*your CSS Rules*/     
}
@media only screen and (min-width: 768px) {
    /*your CSS Rules*/     
}       
@media only screen and (min-width: 960px) {
    /*your CSS Rules*/ 
}
```

Look at the example located in the [mobile_first file](html/mobile_first.html) so that you see the webpage and open the code in a Code Editor. In the code, you'll see code that hides elements, changes font size, and more based on a mobile-first approach. Play around with the code. Add your own responsive features. View it in the browser as a webpage to see your changes.


## [Self Study](#self-study)

Try learning about pseudo elements on your own. Using pseudo elements, you can target specific parts of an element when applying style. The [CSS Pseudo Elements W3Schools](https://www.w3schools.com/css/css_pseudo_elements.asp) page is a great resource, and so is [W3.org page about css pseudo elements](https://www.w3.org/TR/css-pseudo-4/). Also check out this article about [pseudo elements that people overlook](https://blog.logrocket.com/5-css-pseudo-elements-you-never-knew-existed/).
