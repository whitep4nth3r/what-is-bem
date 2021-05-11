# What is BEM in CSS?

This is a small explainer repository that shows how to use the BEM syntax in CSS.

## Why use BEM?

Have you ever worked on an application with one huge CSS file and found that when you changed a style rule in one place, something unexpected happened somewhere else? I had this problem a lot in my early days of front end development. It was frustrating! So what can you do to stop this from happening?

## You need to scope your style rules!

To scope your CSS means to encapsulate style rules in a systematic way so that they apply to one particular chunk of HTML only. CSS-in-JS solutions such as Styled Components or CSS modules that ship with front end frameworks have largely solved this problem by scoping styles to your component templates as standard. This means you don't need to worry about classes in one component affecting the styling of another component — even if you use the same class name. Nice!

But what if you're just starting out, and you want to focus on building out pure CSS in a systematic way without getting bogged down with CSS-in-JS?

## Working in pure CSS

In order to scope your styles in pure CSS, the aim is to declare your CSS classes specifically and solely for individual HTML components. Style rules should be purposefully verbose and self-documenting, without relying on inheritance or default browser behaviour. This type of system discourages the use of utility classes reused across multiple components because this is where you can run into the problems described at the beginning of the post. If you change the style properties of a utility class used in multiple components, *it could affect the layout of your whole application* — sometimes with very undesirable results!

Let's take a look at how we can harness the power of a system like BEM.

## What does BEM stand for?

BEM stands for **block**, **element**, **modifier**, and it's a super-handy system to help you scope CSS style properties to blocks of HTML. What's more, it encourages you to make your HTML and CSS descriptive and self-documenting — helping identify the purpose and intended function of the CSS classes in the code itself.

Other class naming conventions exist alongside BEM to help you scope styles when writing HTML and CSS — such as OOCSS and SMACSS. You can even roll your own system! But the most important thing to remember is to use a system, stick to that system, and *make it work for you*.

So, how do we work with BEM?

## Block, element, modifier

Let's take a look at the building blocks of BEM.

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

### BEM syntax conventions

- Use one or two underscores to separate the block name from the element name
- Use one or two dashes to separate the element name and its modifier
- Use descriptive class names in *camelCase*

## BEM in context

In context, your HTML using the above class names might look like this:

```html
<section class="block">
  <p class="block__elementOne">This is an element inside a block.</p>
  <p class="block__elementOne--modifier">This is an element inside a block, with a modifier.</p>
</section>
```

In a real-life example, with more realistic class names, this might look like:

```html
<section class="container">
  <p class="container__paragraph">This is a paragraph inside a container.</p>
  <p class="container__paragraph--bold">
    This is an paragraph inside a container, with a modifier that adds bold styling.
  </p>
</section>
```

Using the fully-declarative approach, where you don't rely on inheritance or default browser styles, your CSS classes might look like this:

```css
.container {
  display: block;
  margin: 1rem auto;
  padding: 1rem;
  box-sizing: border-box;
}

.container__paragraph {
  color: #000000;
  font-family: Arial, Helvetica, sans-serif;
  font-size: 1rem;
  font-weight: normal;
  line-height: 1.2;
  margin: 0 0 1rem 0;
}

.container__paragraph--bold {
  font-weight: bold;
}
```

Notice how any default browser behaviour we might take for granted has been declared in the above classes — such as `display: block` on the `.container <div>` element. This is an extremely useful way to ensure that if you need to switch up the HTML elements in your components — for example swapping the `<div>` (default `display: block`) for a `<span>` (default `display: inline`) in the above example — the resulting styles of your components are not affected.

## Wrapping up

Using BEM is not going to solve *all* your CSS problems (good luck with centring those `<div>` elements in your layouts!), but it can help you take a step in the right direction to making your CSS readable, descriptive, and safe from any unexpected results. Again, the most important thing to remember is to use a system, stick to that system, and `make it work for you`.
