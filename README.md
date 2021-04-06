# What is BEM in CSS?

This is a small explainer repository that shows how to use the BEM syntax in CSS.

## Why use BEM?

Ever worked on some code with one huge CSS file and when you change something in one place, something unexpected happens somewhere else? I had this problem A LOT in my early days of front end development. It was frustrating! So what can you do to mitigate this?

CSS-in-JS has largely solved this problem, where packages such as Styled Components or CSS modules take care of scoping styles to your component templates rendered in the DOM, meaning you don't need to worry about classes in one component affecting another — even if you use the same class name.

But what if you're just starting out, and you want to focus on building CSS in a systematic way without getting bogged down with CSS-in-JS?

BEM is a really handy way to get used to scoping your styles to blocks of HTML. What's more, it makes the HTML much more descriptive, and helps people identify the purpose and intended function of the CSS classes in the code itself.

## What does BEM stand for?

BEM stands for **block**, **element**, **modifier**.

### Block: a chunk of HTML that you want to scope styles to

```css
.block {
}
```

### Element: any element inside that block, namespaced with your block name

```css
.block__elementOne {
}

.block__elementTwo {
}
```

### Modifier: a flag to add styles to an element, without creating a separate CSS class

```css
.block__elementOne--modifier {
}
```

Notes:

- It's not entirely necessary to use double underscores or double dashes, but it helps to make your code more readable
- The standard syntax for class names in BEM uses camelCase

## BEM in context

In context, your HTML might look like:

```html
<section class="block">
  <p class="block__elementOne">This is an element inside a block.</p>
  <p class="block__elementOne--modifier">This is an element inside a block, with a modifier.</p>
</section>
```

In a real- life example, with more realistic class names, this might look like:

```html
<section class="container">
  <p class="container__paragraph">This is a paragraph inside a container.</p>
  <p class="container__paragraph--bold">
    This is an paragraph inside a contianer, with a modifier that adds bold styling.
  </p>
</section>
```

Using BEM is not going to solve _all_ your problems, but it can help you take a step in the right direction to making your CSS readable, descriptive, and safe from clashing style properties.

It's also worth mentioning that there are plenty of other systems out there to make your life easier when writing HTML and CSS — but the most important thing to remember is to use a system, stick to that system, and make it work for you.
