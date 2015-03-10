# Tindle Digital Styleguide [BETA]

Our CSS has undertaken quite a few twists and turns over the last year, especially as other Styleguides have been made avaliable. AS We develop this styleguide i'll make it clear where some of our inspriration comes from, one main influence is the [Trello Styleguide](https://gist.github.com/bobbygrace/9e961e8982f42eb91b80#file-trello-css-guide-mdllo!)

There are a few main rules governing how we are writing CSS, they are:

* All naming conventions must describe what they are and be as short as possible.
* Only use classes not IDs.
* Write as little as possible.

## How it is written

Using BEM (Block Element Modifier) in this way.

* .block (the name of the object)
* .block__element (the name of a component that is inside that object)
* .block__element.mod-modifier (modifies that component to make it resuable in other ways)
* .block.mod-modifier (modifies that component to make it resuable in other ways)
* .block__element.state-alert (also used to modify the block)

## How can we use this?

You can apply .mod-modifier to modify the object or the component as such:
```css
.block.mod-modifier
.block__element.mod-modifier
```

And in the HTML it would like like this for the first line above:

```html
<div class="block mod-modifier">

</div>
```

# Reducing Specifity

Rather than digging through the dirt to get our styles applied we will use reusable but specific conventions, for example:

1. Not this: `nav ul li li a:link`
2. But rather something like this: `.nav-primary__link`

### To elaborate we wont do this:

```css
nav {}
nav ul {}
nav li {}
nav li a:link {}
```

```html
<nav>
  <ul>
    <li><a href="#">Link 1</a></li>
    <li><a href="#">Link 2</a></li>
    <li><a href="#">Link 3</a></li>
  </ul>
</nav>
```

### An imporvement would be this:

```css
.nav-primary {}
.nav-primary ul {}
.nav-primary li {}
.nav-primary li a:link {}
```

```html
<nav class="nav-primary>
  <ul>
    <li><a href="#">Link 1</a></li>
    <li><a href="#">Link 2</a></li>
    <li><a href="#">Link 3</a></li>
  </ul>
</nav>
```

### A greater imporvement would be this

```css
.nav-primary {}
.nav-primary__list {}
.nav-primary_list-item {}
.nav-primary_list-item-link {}
.nav-primary_list-link.state-selected {}
```

```html
<nav class="nav-primary>
  <ul class="nav-primary__list">
    <li class="nav-primary_list-item"><a class="nav-primary_list-link state-selected" href="#">Link 1</a></li>
    <li class="nav-primary_list-item"><a class="nav-primary_list-link" href="#">Link 2</a></li>
    <li class="nav-primary_list-item"><a class="nav-primary_list-link" href="#">Link 3</a></li>
  </ul>
</nav>
```

We think this also has the benefit of imporvoing performance as the browser doesnt have to work so hard to finsd the appropriate CSS rules.
