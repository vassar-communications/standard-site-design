
In brief
☰☰☰☰☰☰

I've set up the Admissions/Congrats/New Students styling

Short term: If you need something added, contact me.




 - Write this up as a Word doc
 - Set up a Word doc for the different templates I think we need for the new site
 - Have a page that links to these



Philosophy
☰☰☰☰☰☰☰

This system is based in the following basic ideas:

 - Organize CSS files according to a hierarchy that ranges from very generic to very specific.



 - Build as generically as possible, and re-use as much as possible.

Instead of designing very purpose-specific things that can only be used once—say, a self-contained module with its own button styling, module-specific type styling, etc—focus on designing more generic parts (a button, a set of differently sized type styles) that can be assembled into modules. This may not always be possible—some things do require specific treatments—but building generic, re-usable pieces should be the overall goal.

While most if not all modern CSS methodologies are based on some form of building generic, re-usable components, this system is based on these particular ways of working:

 - Object-Oriented CSS.

 - Atomic Design, by Brad Frost. 


Development practices
========

EXTENDS VS VARIABLES: I've been using @extend more than CSS variables. That's a standard object-oriented technique: have generic base objects, and then build off them when you need something more specific. This is also used by other frameworks, such as the Susy grid library.

One of the main benefits of this is that a CSS variable can only impart one value; @extending a class can bring with it a whole set of behaviors. Some examples:

 - Typography. The CSS font shorthand property doesn't include such things as text-transform or letter-spacing; these couldn't be included in a variable. What's more, if you needed the type on a specific element to get smaller depending on the screen size, you couldn't define different sizes in a variable; you'd need several. @extending a class solves all that, since the base class can have whatever behavior you need. That includes breakpoints: you could have a .scaling-headline class that includes different sizes at different breakpoints, and apply it to whatever you need.



Benefits
========

 - 
 
 - Fixing problems is faster, because more components use the same styling. If all your burgundy buttons @extend a class that gives them a particular hover state, and you want to 




Organization
☰☰☰☰☰☰☰☰

The design system has three basic categories: structure, theme, and typography. This correlates to the categories we're already used to working with: layout, color, and type.

So why are the first two called something different? Because they'll contain things that aren't just layout or color.


I'm separating these out to make them re-usable. A module where type and color are rolled together


Structure
=========

Structure contains everything related to the overall structure of the site. By "structure", I mean how items are laid out on a page: where they're positioned, how wide or narrow they are, how much padding they have, etc. While this includes page layouts, it also includes things that are more generic than page layouts, such as:

 - Helpers. These are classes - things like "align-right", "width-wide", and "width-quarter". These aren't layouts in the sense that they contain anything, but they do modify the structure of items on the page.
 
 - Atoms. Atoms serve the same purpose here 
 
 - Modules.
 
 - Layouts. These occupy an odd position in the hierarchy: they're too general to be modules, and too content-specific to go in templates.
 
 - Templates
 
Note: There is currently a folder called "sections".



Typography
==========


Type won't be contained in modules any more - that leads to "font-size: 0.9em" being defined a bunch of times.

Ideally, most modules will use the same collection of styles

For typography, I'm following the same object-oriented approach taken in structure:

 - Generic type styles: "atoms"
 - Combinations: "styles"
 - Uses. This is 


Atoms
-----


Styles
------


So you wouldn't have a class of .label here, because the same styling that goes into

To apply specific styles to elements, we have "uses".



Uses
----

This is where styles are bound to specific markup.







Theme
=====

Theme contains all styling that defines the site aesthetic. This is typically color, although it can also include animations and transitions.

 - Helper classes. In this case, the helper classes define a visual attribute rather than a structural one. The only helper class right now is one that removes a border from an element. These helper classes are useful for edge-case tweaks: something that typically has a border but, under certain conditions, shouldn't have it.
 
 





Techniques
☰☰☰☰☰☰☰


Why should each helper class get its own file? Aren't they very simple?
=============

Well...not always. Sometimes the element they're applied to isn't the element they're targeting, and sometimes their underlying code may need to work differently depending on what they're applied to.

 - For a simple element, like a figure, it's straightforward: apply a class of width-half and it sets that element's width to 50%.
 
 - But imagine you want a 


*** Use @extend for things that are currently defined by CSS variables. ***





















