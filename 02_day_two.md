# Day 2: HTML and CSS Basics

In this lesson, you learn about the `position` style property and its cousins `top`, `right`, `bottom`, and `left`. Those are great for positioning a single element with precision. Next, you practice working with media queries. Media queries are a very useful tool in responsive web design. They let you change an element's style based on the screensize. Then, you learn about CSS animations. Use transitions and keyframes to animate elements on your page.

By the end of this lesson, you will have:

- Experience using the `position` style property
- The basics of using media queries
- An intro to CSS animations
- Self study idea for finding loaders and other animations


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


## [Media Queries](#media-queries)  

Media queries are used in responsive web design to help customize the view based on the user's screensize. In other words, media queries allow you to set HTML element properties that depend upon whether a certain condition is true. For purposes of responsive web design, usually that contidion is the screen width. So, for instance, you can choose for an element to have `font-size: 28px` when the screen is greater than `760px` wide and `font-size: 24px` when the screen is less than or equal to `760px`. This means that you can design webpages that look great on phones, tablets, and computers of all sizes.

### Media Query Syntax and Example

This section focuses on media queries for responsive web design. You write media queries in your CSS code. The syntax for media queries requires `@media` followed by a condition and then an object containing CSS classes. The CSS classes in the media query must be below its corresponding class in the [CSS document](https://stackoverflow.com/questions/7859336/why-are-my-css3-media-queries-not-working).

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

Look at the example located in the [mobile_first file](html/mobile_first.html) file so that you see the webpage and open the code in a Code Editor. In the code, you'll see code that hides elements, changes font size, and more based on a mobile-first approach. Play around with the code. Add your own responsive features. View it in the browser as a webpage to see your changes.

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
