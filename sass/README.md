OnionKnight
===========

SCSS Framework for BEM / SMACSS projects (and the bravest Lost Boy in all of Lordran)

**Dependencies:**
Compass http://compass-style.org  
Susy http://susy.oddbird.net/


SMACSS Architecture
-------------------
see: http://smacss.com/book/categorizing

By categorizing CSS rules, we begin to see patterns and can define better practices around each of these patterns.

There are five types of categories:

    Base
    Layout
    Module
    State
    Theme



**Base rules**   
are the defaults. They are almost exclusively single element selectors but it could include attribute selectors, pseudo-class selectors, child selectors or sibling selectors. Essentially, a base style says that wherever this element is on the page, it should look like this.  
including: Resets, Variables, Tag Styles / Basic Typography, Non-site-specific Modules  
*eg: reset.scss, variables.scss, tags.scss, global-modules.scss*


**Layout rules**
divide the page into sections. Layouts hold one or more modules together.  
including: Grids, any common layout patterns  
*eg: grids.scss, layout-patterns.scss*


**Modules**
are the reusable, modular parts of our design. They are the callouts, the sidebar sections, the product lists and so on. Modules sit inside Layout components. Modules can sometimes sit within other Modules, too. Each Module should be designed to exist as a standalone component.  
including: Blocks & Elements - any visual characteristics needed to describe these (NOT layout - extend a layout pattern from above)  
*eg: modules.scss*
 
 
**State rules**
are ways to describe how our modules or layouts will look when in a particular state. Is it hidden or expanded? Is it active or inactive? They are about describing how a module or layout looks on screens that are smaller or bigger. They are also about describing how a module might look in different views like the home page or the inside page. A state is something that augments and overrides all other styles.  
including: Modifiers/overrides  
*eg: button-states.scss, notification-states.scss*


**Theme rules**
are similar to state rules in that they describe how modules or layouts *might* look. Most sites don’t require a layer of theming but it is good to be aware of it.  
including: Overrides  
*eg: xmas-theme.scss, mothers-day-theme.scss*


BEM Naming Conventions
----------------------
see: http://bem.info/method/definitions/

BEM stands for Block, Element, Modifier.

One of the most common examples of a methodology in programming is Object-Oriented Programming. It's a programming paradigm embodied by many languages. In some ways, BEM is similar to OOP. It's a way of describing reality in code, a range of patterns, and a way of thinking about program entities regardless of programming languages being used.

We used BEM principles to create a set of front-end development techniques and tools, that allow us to build websites quickly and maintain them over a long time.

Written as:    

```CSS
    .block-name__element-name_modifier-key_modifier-value    
```

**Block**
A block is an independent entity, a "building block" of an application. A block can be either simple or compound (containing other blocks).

**Element**
An element is a part of a block that performs a certain function. Elements are context-dependent: they only make sense in the context of the block they belong to.


**Modifier**
To avoid developing another block that is only minimally different from an existing one, we can use a modifier. A Modifier is a property of a block or an element that alters its look or behavior. A modifier has a name and a value - note these should be semantic names and not directly regurgitating css properties, because the visual display of an element may change later on in development.


OnionKnight filestructure
-------------------------

    SCSS >

        screen-modern.scss (compiles all scss for modern browsers)

        screen-legacy.scss (compiles all scss for IE8 and below)

        Base >

            variables.scss

            reset.scss
            
            fonts.scss

            tags/typography.scss

            snippets.scss (non-site-specific tools & modules)

        Layout >

            grids.scss

            common-layout.scss (layout patterns for extending into modules)

        Modules (blocks & elements) >

            common-modules.scss (site specific blocks)

            homepage.scss

            contact.scss

            products-page.scss

            e-commerce-modules.scss

            logical-part-of-the-site.scss (and so on...)

        State (modifiers) >

            button-states.scss

            notification-states.scss

            and so on... (hovers, actives, tag states, opened, hidden, etc?)

        Themes (IE stylesheets count as a theme)

            example-holiday.scss

            IEx.scss

        shame.scss (included last)


Example HTML
-------------------------

```HTML

    <link rel="shortcut icon" type="image/x-icon" href="/images/favicon.ico" />
    <link rel="icon" type="image/png" href="/images/favicon.png" />
    
    <!-- Standard iPhone -->
    <link rel="apple-touch-icon-precomposed" sizes="57x57" href="/images/favicon-low-57.png" />
    <!-- Retina iPhone -->
    <link rel="apple-touch-icon-precomposed" sizes="114x114" href="/images/favicon-high-114.png" />
    <!-- Standard iPad -->
    <link rel="apple-touch-icon-precomposed" sizes="72x72" href="/images/favicon-low-72.png" />
    <!-- Retina iPad -->
    <link rel="apple-touch-icon-precomposed" sizes="144x144" href="/images/favicon-high-144.png" />
        
    <!--[if !IE]> -->
        <?= css('/css/screen-modern.css') ?>
    <!-- <![endif]-->

    <!--[if lte IE 8]>
        <?= css('/css/screen-legacy.css') ?>
    <![endif]-->

    <!--[if gte IE 9]>
        <?= css('/css/screen-modern.css') ?>
        <?= css('/css/ie9.css') ?>
    <![endif]-->


    <!--[if IE 8]>
        <?= css('/css/ie8.css') ?>
    <![endif]-->

    <!--[if IE 7]>
        <?= css('/css/ie7.css') ?>
    <![endif]-->
```
