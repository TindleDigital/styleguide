# Tindle Digital Styleguide Outline

So far we have built a BETA website without worrying to much about following CSS conventions such as B.E.M. This has allowed the freedom to explore the design without getting too carried away on what the code looks like and how to maintain it, we followed a few rules of course to keep some order. 

Over the last few months the goal has been to turn our attention back to the CSS and HTML and reverse engineer a more maintainable and scalable architecture. Much of what we are doing now is heavily influenced by the 2 styleguides below, so thanks to those guys!

[Trello Styleguide](https://gist.github.com/bobbygrace/9e961e8982f42eb91b80#file-trello-css-guide-mdllo!)

[Medium Styleguide](https://gist.github.com/fat/a47b882eb5f84293c4ed)


## Below i'll explain ow we'll be writing our CSS

The use of 1 hyphen is simply to make a compoenents name more readable if more than one word is needed. camelCase was also considered but for now was decided against. All component names need to be as short as possible providing the meaning is still clear. If the word reads just as well without hyphens then leave them out.

    .page-head { }
    .pg-head { } probably just as understandable and readable.

Two hyphens indicate a sub component (or desendant) of a component. Elsewhere you might see this done as .page-head__masterhead This is a bit of a jerky reading experience hence opting for the double dashes.

    .page-head--masterhead { }
    .pg-head--masterhead { } (just as understandable?)
    .pg-head--logo { }

Naming conventions need to describe what it is then it's importance or role. It is essinatial that these words make sense and are clear what they do. For example multiple navigation uses might be as such:

    .nav-primary { }
    .nav-secondary { }
    .nav-dropdown { }

### Utilities

Utilities are resuable anywhere you need them, designated with a u- prefix. they typically are not styleistic in a design way but common layout "helpers".

    .u-utility-name { }
    .u-pull-left { }
    .u-clearfix { }

### Mixins

Mixins offer reusable styles that are common accross the website helping maintain the DRY rule. Use  m- to signal what the class does.

    .m-border-top { }
    .m-brand-colour { }

### Modifiers 

To modify a component's core styles.

    .button { }
    .button.mod-button-lrg { } (inherits components style and modifies it)

In HTML would look like:

    <a class="button">Click</a>
    <a class="button mod-button-lrg">Click</a>

### State

Altered State of elelemt, similar to modifiers but for hightlighting a change in state, for example something is selected or "alert" text is needed.

    .button { }
    .button.is-button-select { }

### Specifity

Keep specificty to a minimum, this improves perfomance and makes code more readable.

    So we can use: .user-list > a:hover { } (supported IE8 up)
    Instead of: ul .user-list li span a:hover { }

### Layout

When it comes to the layout and componenets on the page we want to give the various zones some hirachy something like the below:

    Regions = Main parts of the page (eg: header, nav, content, sidebar and footer),
    Blocks = Places that hold and orgainse the layout of components within a region. May not be called "region" but named by what they are doing.
    Components = Anything in a region or block that isnt layout such as a list.
    
### Use of IDs

IDs are only to be used for functional purposes, we are using ColdFusion and JavaScript, also a prefix identifies which.

    cf-doThis
    js-doThis

### Use of HTML5

We wont be hooking into HTML5 tags directly unless it is for smaller projects, this way we keep our CSS and HTML clearly seperate. 


