## Tindle Digital Styleguide

Our CSS has undertaken quite a few twists and turns over the last year, especially as other Styleguide have been made avaliable.

There are a few main rules governing how we are writing CSS, they are:

1. All naming conventions must describe what they are and be as short as possible.
2. Only use classes not IDs.
3. Write as little as possible.

# How it is written

Using BEM (Block Element Modifier) in this way.

1. .block (the name of the object)
2. .block__element (the name of a component that is inside that object)
3. .block__element.mod-modifier (modifies that component to make it resuable in other ways)
4. .block__element.state-alert (creates an altered state such as highlighting text as an alert)

# How can we use this?

You can apply .mod-modifier to modify the object or the component as such:

1. .block.mod-modifier
2. .block__element.mod-modifier
3. 

# Reducing Specifity

Rather than digging through the dirt to target HTML we will use reusable but specific conventions, for example:

1. Not this: nav ul li li a:link
2. But rather something like this: .nav-primary__link

### To elaborate we wont do this:

nav {}
nav ul {}
nav li {}
nav li a:link {}

<nav>
  <ul>
    <li><a href="#">Link 1</a></li>
    <li><a href="#">Link 2</a></li>
    <li><a href="#">Link 3</a></li>
  </ul>
</nav>

### An imporvement would be this:

.nav-primary {}
.nav-primary ul {}
.nav-primary li {}
.nav-primary li a:link {}

<nav class="nav-primary>
  <ul>
    <li><a href="#">Link 1</a></li>
    <li><a href="#">Link 2</a></li>
    <li><a href="#">Link 3</a></li>
  </ul>
</nav>

### A greater imporvement would be this:

.nav-primary {}
.nav-primary__list {}
.nav-primary_list-item {}
.nav-primary_list-item.state-selected {}

<nav class="nav-primary>
  <ul class="nav-primary__list">
    <li class="nav-primary_list-item state-selected"><a href="#">Link 1</a></li>
    <li class="nav-primary_list-item"><a href="#">Link 2</a></li>
    <li class="nav-primary_list-item"><a href="#">Link 3</a></li>
  </ul>
</nav>

We think this also has the benefit of imporvoing performance as the browser doesnt have to work so hard to finsd the appropriate CSS rules.
