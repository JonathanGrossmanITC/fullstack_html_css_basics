# Day 2: HTML and CSS Basics

In this lesson, you learn about the `position` style property and its cousins `top`, `right`, `bottom`, and `left`. Those are great for positioning a single element with precision. Next, you practice working with media queries. Media queries are a very useful tool in responsive web design. They let you change an element's style based on the screensize. Then, you learn about CSS animations. Use transitions and keyframes to animate elements on your page.

By the end of this lesson, you will have:

- Experience using the `position` style property
- The basics of using media queries
- An intro to CSS animations
- Self study idea for finding loaders and other animations

## [Flexbox](#flexbox)

Flexbox provides an efficient way to organize multiple HTML elements on a webpage in a column *or* row (i.e, in one dimension). In later chapters, you learn about positioning a single HTML element using the `position` property and about positioning multiple HTML elements on a webpage in a grid of rows *and* columns (i.e, two-dimentions).

Flexbox isn't just one style property. Rather, it consists of a collection of CSS style properties that can be used together. When using flexbox, you turn one element into a flex container. The elements in that container will then display flex behavior, meaning that the container element can adjust the height, width, direction, and order based on the space available in the container and other considerations. 

Flexbox's behavior makes it a good choice when working with dynamic content. An example of its dynamic behavior, based on the screensize, is when a flex container expands an interior element's width to fill available free space due to a large screensize. In contrast, it also can shrink an interior element's width to prevent overflow. It can even handle elements that have dynamic size values, like `%` and wrap elements when the parent container lacks enough space to fit all in one row or column (which can make it's one-dimensional structure look like a grid). 

Flexbox's dynamic behavior also allows you to write code that changes orientation, direction, and proportion based on screensize or other factors. In contrast, using display properties of `block` or `inline` restrict you to top-bottom or left-right directions. This will make more sense when you see some examples.

Flexbox style properties are divided into two main categories: (1) those for the container element; (2) those for the interior elements. 

### Parent Flexbox Properties

Many powerful parent flexbox properties exist. The main parent flexbox property you should know is `display: flex`. Setting the `display` property to `flex` turns an HTML element into a flexbox container. Without it, the other flexbox properties won't work. 

Inside a flex container, elements are aligned on the main axis. The main axis of a `div` is the `x-axis`, so the elements inside a `div` flexbox container will appear next to each other by default. Note that the flex container influences only the elements and content directly inside it. Not the elements inside those elements. 

Here is an example of a CSS class with its `display` property set to `flex`.

```css
.buttons-wrapper {
  border: 1px solid black;
  display: flex;
  margin: 5px;
}

.button {
  background-color: gray;
  border-radius: 10px;
  margin: 5px;
  padding: 10px;
}
```

In this example, the `.buttons-wrapper` class has its `display` property set to `flex` and a `border` and `margin`. The `.button` class has a background color, border-radius, margin, and padding. Here is the corresponding HTML:

```html
<!DOCTYPE html>
<html>
  <head>
    <link rel="stylesheet" href="../css/flexbox.css" />
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
    <div class="buttons-wrapper">
      <div class="button">Start</div>
      <div class="button">Pause</div>
      <div class="button">End</div>
    </div>
  </body>
</html>
```
The relevant elements are the `div` with its `class` set to `"buttons-wrapper"` and also the `div` elements inside it with their `class` set to `"button"`. Notice that the three buttons are nested inside the buttons-wrapper. Here is how the example looks in the browser:

![](images/flexbox_one_photo.png)

Notice that the flex container takes up the entire line and that the three interior HTML elements appear next to each other on the x-axis.

Other display properties of the parent include `justify-content` and `align-items`. Used alone or in combination, you can position the interior elements within the flex container. For instance, you can center the interior elements either horizontally, vertically, or both. You also can position them all to the left, top, right, or bottom of the flex container.

The `justify-content` property lets you position items along the main axis. The `align-items` property lets you position items along the cross axis. In the example above, the `x-axis` is the main axis and the `y-axis` is the cross axis. To center the elements along the `x-axis`, use `justify-content: center`. To center the elements along the `y-axis`, use `align-items: center`. Modifying the CSS might look like this:

```css
.buttons-wrapper {
  align-items: center;
  border: 1px solid black;
  display: flex;
  height: 100px;
  justify-content: center;
  margin: 5px;
}

.button {
  background-color: gray;
  border-radius: 10px;
  margin: 5px;
  padding: 10px;
}
```
In the modified example above, you added `align-items`, `height`, and `justify-content` properties to the `.buttons-wrapper` class. The two flexbox properties are set to values that center the interior buttons and the `height` property is there to make it more obvious that the buttons are vertically centered. Here's what it looks like in the browser.

![](images/flexbox_two_photo.png)

In addition to positioning *elements* inside a flexbox container, you can use the technique above to position *text* horizontally and/or vertically inside an element. For instance, you could turn the `.button` class into a flex container with `align-items` and `justify-content` set to `center`. Then, the text inside the `.button` will appear in the middle of the button.

Centering is just one way you can position elements or text within a flex container. You also can align items at the start or end of the container. Plus, the parent container has many other flexbox options, like `flex-direction` and `flex-wrap`. Check out [this great flexbox guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/).

A note on `flex-direction` -- it flips which axis is the main and which is the cross access. This results in `align-items` and `justify-content` controlling whichever axis it didn't control by default instead of its default axis. In the example above, adding `flex-direction: column` to the `div` results in `align-items` controlling horizontal orientation of the child elements and `justify-content` controlling the vertical (the opposite of the default on a `div`).

### Child Flexbox Properties

The children elements in a flexbox container also have their own properties. For instance, `flex-grow` and `flex-shrink` allow you to increase or decrease the size of an interior element based on the available space in the container. Each of them accept an integer as a value. That value determines the proportion of available space the item should occupy.

For example, for `flex-grow`, if all interior elements are `flex-grow: 1`, any extra space in the container will be distributed equally. If, however, one of the children is `flex-grow: 2`, it would try to occupy twice as much space as the others.

Here is an example CSS:

```css
.buttons-wrapper {
  align-items: center;
  border: 1px solid black;
  display: flex;
  height: 100px;
  justify-content: center;
  margin: 5px;
}

.button-start {
  background-color: green;
  border-radius: 10px;
  flex-grow: 1;
  margin: 5px;
  padding: 10px;
}

.button-pause {
  background-color: yellow;
  border-radius: 10px;
  flex-grow: 2;
  margin: 5px;
  padding: 10px;
}

.button-end {
  background-color: red;
  border-radius: 10px;
  flex-grow: 1;
  margin: 5px;
  padding: 10px;
}
```

This is a similar example to the ones before, but now you have three button classes. The `.button-start` and `.button-end` classes each have `flex-grow: 1` and the `.button-pause` class has `flex-grow: 2`. The HTML file in this example is basically the same as before, except now the new CSS class names for the buttons are matched to the corresponding HTML element. 

Here's what it looks like in the browser:

![](images/flexbox_three_photo.png)

See that the pause button (i.e., the one with the `.button-pause` class) takes up twice as much extra space as the other two. 

Another common thing to do is set the child's `align-self` or `justify-self` properties to override the `align-items` or `justify-content` properties, respectively, as applied to that child. It essentially takes that child out of the normal flow. This is good, for example, if you want all elements centered in the flex container except for one of the elements. You can use`align-self` or `justify-self` on that child to position it.  

There is a lot more you can do with child components CSS flex properties, like even set the order in which they align themselves. Again, check out [this great flexbox guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/).

Other resources that might help are [MDN's flexbox basics](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox), [W3 Schools Flexbox](https://www.w3schools.com/css/css3_flexbox.asp), and [Flexbox Frogger](https://flexboxfroggy.com/).  


## [Position Style Property](#position-style-property)  

The `position` style property allows you to control where an element is positioned on the page. The default value for `position` is `static`. This means that elements render in order as they are written in your code. You can override the default value to [position elements](https://www.w3schools.com/cssref/pr_class_position.asp) relative to specific elements on your page. Your other options for `position` are the values `absolute`, `relative`, `fixed`, and `sticky`. Here is an example of three classes:

```css
.header-title {
  font-size: 24px;
}

.header-subtitle {
  font-size: 24px;
  position: static;
}

.footer {
  font-size: 24px;
  position: absolute;
}
```

In the example above, the top two classes (`.header-title` and `.header-subtitle`) are `position: static`. This is the default for both, so you don't need to explicitly declare it. The only difference between the two is that one explicitly declares `position: static` and the other doesn't. Explicitly declaring the default value doesn't change it, and therefore both are `position: static`. The third class (`.footer`) is `position: absolute` because it overrides the default by explicitly declaring `position: absolute`.

Often used in combination with the `position` property are the properties `top`, `right`, `bottom`, and `left`. Their values are in pixels, like `top: 10px`, and are used with `position` to place HTML elements on the page. The properties `top`, `right`, `bottom`, and `left` influence an element only if the element is *positioned*. An element is positioned only if its `position` is anything other than `static`.

Using `top`, `right`, `bottom`, and `left` in combination with the `position` values other than `static` allow you to position an element with precision regardless of where its default position would be. To better understand how the `position`, `top`, `right`, `bottom`, and `left` values behave, here are a few notes and examples. 

When `position` has its default value of `static`, if you set `top`, `right`, `bottom`, and `left`, the `position: static` element responds to the document, not to its parent. Accordingly, statically positioned elements aren't influenced by `top`, `right`, `bottom`, and `left` values.

In contrast, the `absolute` value positions an element relative to its first *positioned* ancestor element. Note the requirement of a *positioned* ancestor. This means the `absolute` element needs to have a ancestor element that also has a `position` property set. For instance, if the parent element has `position: relative`, then the `position: absolute` child element will have properties for `top`, `right`, `bottom`, `left` that refer to the parent element.

```css
.section-wrapper {
  position: relative;
}

.footer {
  font-size: 24px;
  position: absolute;
  bottom: 0px;
  left: 0px;
  right: 0px;
}
```

In the example above, assume the HTML file is such that the `.section-wrapper` element wrap the `.footer` element. The `.footer` class has `position: absolute` and `0px` for each of `bottom`, `left`, and `right`. The `.section-wrapper` is a *positioned* ancestor of the `.footer` element because it is `position: relative` and wraps the `.footer` (i.e., the `position: absolute` element). This results in the `.footer` element appearing at the bottom of the `.section-wrapper` element and spanning that element's entire width.

When `relative`, the element is positioned using `top`, `right`, `bottom`, and `left` relative to its normal position. Because the element is *positioned* (i.e., its `position` is `relative` instead of `static`), it responds to values for `top`, `right`, `bottom`, and `left`. For instance, `position: relative; top: 10px` adds 10 pixels to the element's top position relative to where its position otherwise would be. See this StackOverflow post about [the difference between position static and relative](https://stackoverflow.com/questions/5011211/difference-between-static-and-relative-positioning). As you saw above for `absolute`, setting an element's position to `relative` is also used for *positioning* it so that it can serve as the positioned ancestor for an `absolute` element.

When `fixed`, the browser positions the element relative to the browser window. One effect of this is that the `position: fixed` element does not move when the user scrolls. For instance, a footer with `position: fixed; bottom: 0` will appear at the bottom of the browser even when the user scrolls.

```css
.footer {
  font-size: 24px;
  position: fixed;
  bottom: 0px;
  left: 0px;
  right: 0px;
}
```

In the example above, the `.footer` class has `position: fixed` and `0px` for each of `bottom`, `left`, and `right`. Used in combination, the `position`, `bottom`, `left`, and `right` result in a footer appearing at the bottom of the screen and spanning the entire width of the page, even when the user scrolls. You'll see an example of this in one of html files but for a navbar instead of a footer.

The `sticky` value positions an element relative to the user's scroll position. It exhibits both `relative` and `fixed` behavior. The `sticky` element acts like a `relative` element until the scroll position reaches a specified location in the viewport. Then, the `sticky` element acts like a `fixed` element. It remains in place. An element with `position: sticky; top: 200px;` is relatively positioned until the scroll location causes the element to be `200px` from the top. Then it sticks and remains `50px` from the top, even when the user scrolls.

To better understand the behavior of positioning properties, open in your browser the [positions](html/position.html) file so that you see the webpage (not the source code on GitHub). Open the inspector, and take turns toggling on and off the properties for the `.position-absolute` class of `right`, `bottom`, `left`, `height`, and `width`. Try different combinations of on and off and also try changing their values. See what happens. 

What happens when you change the `position` properties of either class to something else? When you change the `.position-absolute` value for `position` to `fixed`, where do those elements go? Are they both on the DOM? How can you tell?

For more examples and resources, visit [W3 Schools](https://www.w3schools.com/cssref/pr_class_position.asp), [CSS Tricks Position](https://css-tricks.com/almanac/properties/p/position/) and [CSS Tricks Top Right Bottom Left](https://css-tricks.com/almanac/properties/t/top-right-bottom-left/).


## [CSS Animations](#css-animations)  

CSS animations let you change the style of an HTML element. By gradually changing an element's location on the page, size, orientation, and more, you can animate parts of your page.

Two important toolsets for CSS animations are transitions and keyframes. 

### Transitions

A [transition](https://www.w3schools.com/css/css3_transitions.asp) gradually changes one or more property values for a CSS class over a specified period of time. The collection of properties for a transition are `transition-property`, `transition-duration`, `transition-timing-function`, and `transition-delay`. The `transition-property` and `transition-duration` are mandatory and the other two are optional.

The `transition-property` defines which CSS property the transition applies to. The `transition-duration`	defines how long the transition will last.  The `transition-timing-function` defines the speed curve of the transition. Check out the [Cubic Bezier site](https://cubic-bezier.com/#) to learn more. The `transition-delay` defines any delay in seconds before the transition occurs.

You can set one or more of the transition properties all at once using the `transition` property. The order of the values are `transition: <transition-property>, <transition-duration>, <transition-timing-function>, <transition-delay>`. Here is an example of setting the `transition-property` and `transition-duration` using the `transition` property:


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

CSS [animations](https://www.w3schools.com/css/css3_animations.asp) change an element's style over a given time. In an animation , you can change one or more style properties at a time. You use the `@keyframes` rule to name the animation and identify the styles that change and at which time points. Here is an example:

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

As you see in the example, the `@keyframes` block starts with `@keyframes`, followed by the name of the animation, and then `{ }`. Inside are pairs of a `%` and an object of key:value pairs. The `%` corresponds to the point in time of the `animation-duration` and the key:value pairs are CSS styles. In this example, the animation will change the element's `color` and `font-size` at each of 0%, 25%, 50%, and 100% of the `animation-duration` of 4 seconds. 

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

In the example above, the animation is the `@keyframes` named `change-color `, and it will last 5 seconds, have a linear timing function, it will be delayed for 2 seconds, it will run infinitely, and it will alternate directions.

### Examples of Animations

Look at the example located in the [animations file](html/animations.html) so that you see the webpage and open the files in a Code Editor. In the files, you see code that animates the page using keyframes and transitions. Play around with the code to understand how the durations and delays interact with one another. How can you change the CSS properties to improve this? How can you use animations to make loaders and alerts? Add your own responsive features to this start and view your new and improved version in the browser as a webpage!


## [Self Study](#self-study)

You'll most likely want to keep your animations to a minimum, as too many animations can make your page look amateur and also cause performance issues. You will, however, want to use animations at least sometimes. For instance, you'll want to animate loaders. Check out Code Pen's [loaders](https://codepen.io/topic/loader/picks) and other [animations](https://codepen.io/search/pens?q=animations&depth=title). Also consider the [W3Schools page on loaders](https://www.w3schools.com/howto/howto_css_loader.asp).

Try to use a Code Pen animation in your own code or design your own!
