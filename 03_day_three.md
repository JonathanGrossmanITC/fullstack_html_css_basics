# Day 3: HTML and CSS Basics

In this lesson, you learn about CSS animations and Bootstrap. Using CSS animations, you can enhance your designs and improve the user experience. For instance, you can create loaders, alerts, hover effects, and more. You'll learn two different ways to create CSS animations. One way is using **transitions** and the other is using **keyframes**.  

Next, you learn about Bootstrap. It is a popular framework for applying CSS to your HTML elements. Rather than write your own CSS classes, you can import Bootstrap and use their CSS classes. Plus, by learning Bootstrap, you pracice working with external libraries for CSS.

By the end of this lesson, you will have:

- An intro to [CSS animations](#css-animations) using transitions and keyframes     
- An intro to [Bootstrap](#intro-to-bootstrap)  
- [Self study](#self-study) ideas for finding loaders and other animations  


## [CSS Animations](#css-animations)  

CSS animations let you change the style of an HTML element, either when the page loads or triggered by an event on your web page, like a click, input, hover, or other event. By gradually changing an HTML element's design, location on the page, size, orientation, and more, you can animate parts of your page.

Two important toolsets for CSS animations are transitions and keyframes. 

### Transitions

A [transition](https://www.w3schools.com/css/css3_transitions.asp) gradually changes one or more property values for a CSS class over a specified period of time. The collection of properties for a transition are `transition-property`, `transition-duration`, `transition-timing-function`, and `transition-delay`. The `transition-property` and `transition-duration` are mandatory and the other two are optional.

The `transition-property` defines which CSS property the transition applies to. The `transition-duration`	defines how long the transition will last.  The `transition-timing-function` defines the speed curve of the transition. Check out the [Cubic Bezier site](https://cubic-bezier.com/#) to learn more. The `transition-delay` defines any delay in seconds before the transition occurs.

You can set one or more of the transition properties all at once using the `transition` property. For instance, the following sets the `transition-property` as `font-size` and `transition-duration` to 1 second and ignores the other two properties: `transition: font-size 1s`. The order of the values are `transition: <transition-property>, <transition-duration>, <transition-timing-function>, <transition-delay>`. Here is the example in code of setting the `transition-property` and `transition-duration` using the `transition` property:


```css
.footer {
  background-color: gray;
  font-size: 24px;
  position: fixed;
  bottom: 0px;
  left: 0px;
  right: 0px;
  transition: font-size 1s;
}
```

In the example above, the `.footer` class has a `transition: font-size 1s`, which means that the `font-size` will change over the duration of 1 second. You can define transitions for more than one property. To do so, separate the transition statements with a comma, like so:


```css
.footer {
  ...
  transition: font-size 1s, font-weight 2s;
}
```

In this example, the `font-size` will change over the duration of 1 second and the `font-weight` will change over the duration of 2 seconds.

If instead of setting only the property and duration, you want to set three or all four `transition` properties, you can do so easily. An example of setting all four is:

```css
.footer {
  ...
  transition: font-size 1s linear 2s;
}
```

In the example above, the `.footer` class has one transition -- a `font-size 1s linear 2s`. This means that the `font-size` will change over the duration of 1 second using a linear timing function after a delay of 2 seconds. 

Now that you know how to write the transition, you need to know how to trigger it. For the transition to start, you need to something to change the value of the `font-size`. One way to change the value of the font-size is to use a hover effect. Here is an example of the code:

```css
.footer:hover {
  font-size: 28px;
}
```

In the example above, when the user hovers their mouse over the footer, the `font-size` will increase from `24px` to `28px` Rather than change size by its default behavior, the `font-size` will change according to the terms of your `transition`.

In addition to the hover effect, research which other [Pseudo elements](https://www.w3schools.com/css/css_pseudo_elements.asp) you could use with transitions. The [Using CSS Transitions page by MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions) has additional information and [CSS Tricks](https://css-tricks.com/almanac/properties/t/transition/) has some good examples. Also, check out this [list of some simple but powerful techniques](https://www.webdesignerdepot.com/2014/05/8-simple-css3-transitions-that-will-wow-your-users/) for using transitions to animate.

### Keyframes

Like you learned for transitions, use keyframes for CSS [animations](https://www.w3schools.com/css/css3_animations.asp) lets you change an element's style over a given time. With keyframes, you can change one or more style properties at a time. You use the `@keyframes` rule to name the animation and identify the styles that change and at which time points. Here is an example:

```css
/* The animation code */
@keyframes color-change {
  0%   {color: black;}
  25%  {color: white;}
  50%  {color: blue;}
  100% {color: black;}
}
```

After declaring your `@keyframes`, you need to bind it to an HTML element using one of the `animation` subproperties. The collection of subproperties that comprise the `animation` property are `animation-name`, `animation-duration`, `animation-timing-function`, `animation-delay`, `animation-iteration-count`, `animation-direction`, `animation-fill-mode`, and `animation-play-state`. 

You bind the `@keyframes` to an element by setting the `@keyframes` name as the value of `animation-name`. The `animation-name` and also the `animation-duration` are mandatory when making an animation. The`animation-duration` defines how long one iteration of the animation lasts. It's default value is `0s`, so the animation doesn't run unless you override the default value.

To help explain the syntax for an animation, here is an example of an animation:

```css
/* The animation code */
@keyframes color-change {
  0%   {color: black; font-size: 24px}
  25%  {color: white; font-size: 30px}
  50%  {color: blue; font-size: 18px}
  100% {color: black; font-size: 24px}
}

/* The element to apply the animation to */
.footer {
  animation-name: color-change;
  animation-duration: 4s;
  background-color: gray;
  font-size: 24px;
  position: fixed;
  bottom: 0px;
  left: 0px;
  right: 0px;
  transition: font-size 1s; 
}
```

As you see in the example, the `@keyframes` block starts with `@keyframes`, followed by the name of the animation, and then `{ }`. Inside are pairs of a `%` and an object of key:value pairs. The `%` corresponds to the point in time of the `animation-duration` and the key:value pairs are CSS styles for that block of time. In this example, the animation will change the element's `color` and `font-size` at each of 0%, 25%, 50%, and 100% of the `animation-duration` of 4 seconds. 

In the example, at the beginning of the animation the font `color` is black and `font-size` is 24 pixels. Next, after 25% of the duration passes, the font `color` turns white and `font-size` becomes 30 pixels. Then, after 50% duration the font `color` turns blue and `font-size` becomes 24 pixels. Finally, the font `color` turns black and `font-size` returns to 24 pixels after 100% of the animation duration.

The `@keyframes color-change` animation is bound to the the `.footer` class because the `animation-name` for the `.footer` is `color-change` (the name of the `@keyframes`). The animation will last 4 seconds because the `animation-duration` for the `.footer` is `4s`.

As an alternative to using percentages for time, you can use `from` and `to` for a gradual change between two values:

```css
@keyframes two-color-change {
  from {color: black;}
  to {color: blue;}
}
```

In this approach, the font color will change from black to blue gradually over the `animation-duration`.

As for the rest of the animation properties, here are a few notes. The `animation-timing-function` defines the animation's speed curve. Check out the [Cubic Bezier site](https://cubic-bezier.com/#) to learn more about speed curves. The `animation-delay` sets any delay before the animation starts. Negative values are allowed, which results in the animation starting part-way through its duration.

The`animation-iteration-count` defines how many times the animation should be played. You can declare an integer or `infinite`. The `animation-direction`	declares whether an animation should be played forwards, backwards or in alternate cycles. The `animation-fill-mode` defines styles for the element when the animation is not playing. The `animation-play-state` is the status of whether the animation is playing or paused. 

Find out more details about these properties and see some examples at [W3Schools page for CSS animations](https://www.w3schools.com/css/css3_animations.asp).

You can set one or more of the animation properties all at once using the `animation` property. The order of the values are `animation: <animation-name>, <animation-duration>, <animation-timing-function>, <animation-delay>, <animation-iteration-count>, <animation-direction>, <animation-fill-mode>, <animation-play-state>`. Here is an example of setting six of the `animation` properties using the shorthand:

```css
.footer {
  animation: change-color 5s linear 2s infinite alternate;
  ...
}
```

In the example above, the animation is the `@keyframes` named `change-color`, and it will last 5 seconds, have a linear timing function, it will be delayed for 2 seconds, it will run infinitely, and it will alternate directions.

### Examples of Animations

Look at the example located in the [animations file](html/animations.html) so that you see the web page and open the files in a Code Editor. In the files, you see code that animates the page using keyframes and transitions. Play around with the code to understand how the durations and delays interact with one another. How can you change the CSS properties to improve this? How can you use animations to make loaders and alerts? Add your own responsive features to this start and view your new and improved version in the browser as a web page!


## [Intro to Bootstrap](#intro-to-bootstrap)

[Bootstrap](https://getbootstrap.com/) is an open-source framework for stlying mobile-first, responsive web applications. The framework provides pre-written CSS and JavaScript-based templates. For instance, Bootstrap has templates for navigation bars, alerts, buttons, and more. They've written the code, you just import and use it in yours.

### Bootstrap is an example of a CSS Framework  

Bootstrap is important for you to learn because it is the most popular open-source styling framework and also because much of what you learn using Bootstrap can help you learn how to use other style frameworks -- public and private. Accordingly, it is good that you practice using Bootstrap so that you're familiar working with style frameworks generally. 

Many of the things you can do in plain CSS, Bootstrap has one or more pre-written templates that will do it for you (or at least get you close). For instance, you can use Bootstrap classes for [layout](https://getbootstrap.com/docs/4.5/layout/overview/), [content](https://getbootstrap.com/docs/4.5/content/reboot/), [forms](https://getbootstrap.com/docs/5.0/forms/overview/), [components](https://getbootstrap.com/docs/4.5/components/alerts/), and [more](https://getbootstrap.com/docs/4.5/utilities/borders/).

Whether to use Bootstrap, some other style framework, or your own custom CSS depends upon your situation. Sometimes your customer, team, or project will clearly require one over the others, in which case the decision is easy. Other times, you might get to choose. Consider what is most convenient for you in terms of writing clean code that is easy for you and others to maintain and understand.

Regardless of your choice for styling, be consistent throughout your project with your styling patterns. Choose one approach as your predominant way of styling. For instance, if you're using Bootstrap, try to do as much as you can with it instead of half Bootstrap, half custom CSS. It can get confusing if you mix and match Bootstrap with custom CSS or another framework. Accordingly, avoid or minimize the mixing of different style approaches. If you have to do some mixing, do so in a way that is clear, predictable, and easy to understand.  

### Installing 

You need to install Bootstrap in your project. Several ways exist, and the [quick start](https://getbootstrap.com/docs/4.5/getting-started/introduction/) is a great way for many projects. As the instructions in the quick start explain, put the following code in the `head` tag of your HTML document:

```html
<link
  href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta1/dist/css/bootstrap.min.css"
  rel="stylesheet"
  integrity="sha384-giJF6kkoqNQ00vy+HMDP7azOuL0xtbfIcaT9wjKHr8RbDVddVHyTfAAsrekwKmP1"
  crossorigin="anonymous"
/>
```

Also, put the following code at the bottom of your `body` tag in your HTML document:

```html
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta1/dist/js/bootstrap.bundle.min.js" integrity="sha384-ygbV9kiqUc6oa4msXn9868pTtWMgiQaeYH7/t7LECLbyPA2x65Kgf80OJFdroafW" crossorigin="anonymous"></script>
```

The `link` is the Bootstrap stylesheet. It's like when you import your own stylesheet, but this is Bootstrap's. Imgaine how big the stylesheet is! The `script` tag is necessary because many Bootstrap templates require JavaScript. Accordingly, the `script` tag gives you access to the necessary Bootstrap JavaScript code. 

Bootstrap even provides example HTML for you to test. Here is an example using Option 1 from their example, with a Bootstrap button added for effect:

```html
<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-giJF6kkoqNQ00vy+HMDP7azOuL0xtbfIcaT9wjKHr8RbDVddVHyTfAAsrekwKmP1" crossorigin="anonymous">

    <title>Hello, world!</title>
  </head>
  <body>
    <h1>Hello, world!</h1>
    <button type="button" class="btn btn-primary">Primary</button>

    <!-- Option 1: Bootstrap Bundle with Popper -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta1/dist/js/bootstrap.bundle.min.js" integrity="sha384-ygbV9kiqUc6oa4msXn9868pTtWMgiQaeYH7/t7LECLbyPA2x65Kgf80OJFdroafW" crossorigin="anonymous"></script>
  </body>
</html>
```

If you load this HTML file in the browser, you will see this:

![](images/bootstrap_install.png)

Notice the title's font is styled, so is the button, and no errors in the console. No custom CSS. Simply, you import Bootstrap and use their classes. Here, the style comes from the Bootstrap default styling for `h1` and `button` tags, plus their styles from the `btn` and `btn-primary` classes. Instead of looking to CSS documentation and your own stylesheet to figure out what `h1`, `button`, `btn` and `btn-primary` are, you look at Bootstrap's documentation. Examples below.

This installation is a quick and effective approach to working with Bootstrap. Check out other ways to [install Bootstrap](https://getbootstrap.com/docs/5.0/getting-started/download/).

### Examples Using Bootstrap. 

Among the many things you can use Bootstrap for are layout, content and forms, components, and utilities. They have ready-to-use CSS classes for you to use.  

#### Layout

Bootstrap offers templates for page layouts. Bootstrap's layout system relies upon [containers](https://getbootstrap.com/docs/5.0/layout/containers/), rows, and [columns](https://getbootstrap.com/docs/5.0/layout/columns/) to create a [grid-like layout](https://getbootstrap.com/docs/5.0/layout/grid/), and [breakpoints](https://getbootstrap.com/docs/5.0/layout/breakpoints/) to adapt your layout in response to a particular viewport or device size. It is similar to Grid and Flexbox, but it has its own syntax and quirks.

To use Bootstraps layout system, you need to know that it consists of a container element that wraps HTML elements. The wrapped HTML elements serve as rows nested inside the container. The rows have columns nested inside them. 

Containers center and horizontally pad your grid and are the outer-most wrapping element. Rows are elements nested directly inside containers and serve as containers for columns. Rows come with built-in values for `margin` and `padding`. You **must** use rows inside of a container. A good rule, is that if you use a container also use a row directly inside it, and if you use a row, wrap it with a container. 

Columns are nested inside rows. Each row has 12 columns. An element can span any number of the 12 rows. As you see in the Bootstrap examples, the Bootstrap classes for columns (`.col`) allow you to say how many (e.g., `.col-6`) columns that HTML element occupies.

Use Bootstrap's built-in breakpoints to say how many columns an element should occupy depending upon the size of the browser. Bootstrap has six breakpoints. Extra small (`.col-xs-` or `.col-`), small (`.col-sm-`), medium (`.col-md-`), large (`.col-lg-`), extra large (`.col-xl-`), and extra extra large (`.col-xxl-`). The syntax means that the column at whichever designated screen size (and greater) will be the number of columns appearing after the second `-`. For instance, an element with (`.col-md-6`) will be 6 columns wide at medium-sized screens and greater. Below that, it is 12 columns because that is the default. 

You can add more than one breakpoint to an element. Here is an example of [mixing and matching](https://getbootstrap.com/docs/5.0/layout/grid/#mix-and-match):

```html
<div class="container">
  <!-- Stack the columns on mobile by making one full-width and the other half-width -->
  <div class="row">
    <div class="col-md-8">.col-md-8</div>
    <div class="col-6 col-md-4">.col-6 .col-md-4</div>
  </div>

  <!-- Columns start at 50% wide on mobile and bump up to 33.3% wide on desktop -->
  <div class="row">
    <div class="col-6 col-md-4">.col-6 .col-md-4</div>
    <div class="col-6 col-md-4">.col-6 .col-md-4</div>
    <div class="col-6 col-md-4">.col-6 .col-md-4</div>
  </div>

  <!-- Columns are always 50% wide, on mobile and desktop -->
  <div class="row">
    <div class="col-6">.col-6</div>
    <div class="col-6">.col-6</div>
  </div>
</div>
```


Read more about the [Bootstrap grid options](https://getbootstrap.com/docs/5.0/layout/grid/#grid-options) and read more about [how it works](https://getbootstrap.com/docs/5.0/layout/grid/#how-it-works) to learn Bootstrap's grid system.

#### Content and Forms

Bootstrap comes with templates that style the content on your webpage, like text, images, tables, and more. Its styles provide default built-in styles for HTML elements, like the `body`, `h1` to `h6` tags, `form` and others. Simply using the HTML tag with Bootstrap installed will result in the Bootstap style appearing on the browser.  

Bootstrap also provides Bootstrap classes for additional content styling that supplement or override the Bootstrap built-in styling. Use those styles by assigning them to an element's class attribute.

To learn more about Bootstrap content, check out their pages about [typography](https://getbootstrap.com/docs/5.0/content/typography/), [images](https://getbootstrap.com/docs/5.0/content/images/), [tables](https://getbootstrap.com/docs/5.0/content/tables/), and [figures](https://getbootstrap.com/docs/5.0/content/figures/). Be sure to look at the table on the right of each page in the links for content specific to that topic.

Also look at the documentation about [forms](https://getbootstrap.com/docs/5.0/forms/overview/). You'll find examples and guidelines for form control styles, layout options, and custom components for creating forms.

#### Components

Bootstrap provides templates for many components that are common across most webpages. An example is the [button](https://getbootstrap.com/docs/5.0/components/buttons/) you saw earlier. In addition to buttons, Bootstrap offers pre-built [alerts](https://getbootstrap.com/docs/5.0/components/alerts/), [badges](https://getbootstrap.com/docs/5.0/components/badge/), [cards](https://getbootstrap.com/docs/5.0/components/card/), [dropdowns](https://getbootstrap.com/docs/5.0/components/dropdowns/), [navigation](https://getbootstrap.com/docs/5.0/components/navs-tabs/), [spinners](https://getbootstrap.com/docs/5.0/components/spinners/), and more.

The components come in multiple options for size, color, and other properties. Mix and match to make your page look unique.

#### Utilities

Bootstrap has a ton of utility classes that allow you to build upon their other templates or use alone to style an element. Those utility classes include styles for CSS properties like borders, colors, display, flex, position, shadows, size, text, and others. Read about the [Bootstrap utility classes](https://getbootstrap.com/docs/5.0/utilities/colors/) to learn about what you can do with them.

Finally, you can override Bootstrap styles by using your custom CSS. Let's say you want a button of a certain color that you can't find in Bootstrap. Write your own CSS class and apply it to the Bootstrap button element. Make sure you import your CSS file in your HTML file in the `head` below where you import Bootstrap.

## [Self Study](#self-study)

You'll most likely want to keep your animations to a minimum, as too many animations can make your page look amateur and also cause performance issues. You will, however, want to use animations at least sometimes. For instance, you'll want to animate loaders. Check out Code Pen's [loaders](https://codepen.io/topic/loader/picks) and other [animations](https://codepen.io/search/pens?q=animations&depth=title). Also consider the [W3Schools page on loaders](https://www.w3schools.com/howto/howto_css_loader.asp).

Try to use a Code Pen animation in your own code or design your own!  
