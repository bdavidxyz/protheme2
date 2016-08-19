---
layout: post
author: David Boureau
minread: 11
title:  "How to name css classes"
date:   2016-05-18
categories: css
permalink: /blog/:title/
description: "A collection of pragmatic tips, about css class naming, based on curation and work experience"
---


Based on my favorite articles on the topic, and recent work experience, here are my 2 cents about how to properly name CSS classes.


## 0. Before to think about class name, choose a good name for HTML elements

If it's an input, use the _input_ element.

It will be far easier for the reader to scan the HTML document.

**Example :**

```html
<div class='submit'/> <!-- Wooot ? -->
```

```html
<input class='submit'/> <!-- Ah, ok -->
```

**Source** : [Raphael Goetter (french article)](https://blog.goetter.fr/2014/11/10/bien-utiliser-un-framework-css/)

## 1. Put the class name at the lowest possible level

It impacts how classes will be named. Always use the class name directly on the HTML element you want to style, even if seems to cost an extra effort.
Check the article of Chris Coyer below if it is not clear why.

**Example :**

```html
<main class='mainly'>
  <p>Lorem ipsum</p> <!-- I'd like to style this paragraph-->
</main>
```

```css
main.mainly p { /* DON'T DO THIS */
}

/* Instead, assign a class name to p : <p class='paragraphly' /> */
.paragraphly {
}
```

**Source** :  [Chris Coyer](https://css-tricks.com/strategies-keeping-css-specificity-low/#article-header-id-3)


## 2. Use content to find a name

**Example**

```css
.c-header-logo {
  /* Just by reading the name, I guess this selector targets the logo of the header. */
}
```

**Source** : [phpied.com](http://www.phpied.com/css-coding-conventions/)



## 3. Don't use content, if the picture speaks louder

Let's say the header logo actually looks like this :

![Guillotine](http://res.cloudinary.com/toutuncafe/image/upload/c_scale,h_74,w_139/v1463738189/guillotine_cgxbrd.png)

Then don't call it header-logo.

```css
.guillotine {
  /* Oh, I see what we are trying to style */
}
```






## 4. Try *-like* suffix for better reuse.

**Example :**

```css
h3, .h3-like {
/* some styling */
}
```
```html
<p class='h3-title'>
  <!--I am NOT an h3 title, but since designer asked me to look the same,
      I can't complain about my classname-->
</p>
```

**Source** :  [KNACSS v4](http://bit.ly/27GQhS6)



## 5. Don't use camelCase

It makes things harder to read.

**Example :**

```css
.navToOneModuleICreated {
  font-size:2em;
}
/* versus */
.nav-to-one-module-i-created {
  font-size:2em;
}
```

**Source :** [Harry Roberts](http://csswizardry.com/2010/12/css-camel-case-seriously-sucks/)



## 6. Try BEM

It's one of the most commonly used convention by now.

* It looks really weird as first glance, don't be afraid
* The entry cost is extremely low
* You can try it now on any part of existing project
* Long term benefits are huge

(double dash) means variation of the element.
(double underscore) means children of the element.


**Example**

```html
<button class='btn btn--warning'> <!-- .btn--warning one of the variation of .btn-->
  <div class="btn__text"></div> <!-- .btn__text one of the child of .btn-->
</button>
```
```css
.btn--warning {
/* Yay ! By convention, I know that code here relate to the variation "warning" of a button, without event looking at the HMTL code. What a relief !*/
}
.btn__text {
/* For same reason, I know that this style will target text in a button */
}
```

**Source** :  [Kaelig,  fifty shades of BEM](http://blog.kaelig.fr/post/48196348743/fifty-shades-of-bem)

**Recommended** :  [Smashing Magazine, Battling BEM](https://www.smashingmagazine.com/2016/06/battling-bem-extended-edition-common-problems-and-how-to-avoid-them/)


## 7. Try more uglier

BEM opens new possibilities, even if their conventions looks icky at first glance.

But very unusual also means that the eye can quickly grab what is actually happening and where, and for BEM, believe me, it works.

Now you can try more icky convention, as long as you stick to it the whole project.

**Example**

```css
.DIMENSIONS_OF_mycomponent {
  /* Ickier is almost impossible. But now it is more clear what it is about.*/
  /* I used it for SASS placeholder.*/
  /* Don't abuse of this rule, though.*/
}
```

## 8. Use fully descriptive words

Apart from big classics like nav, txt, url... you should avoid any abbreviation.

**Source** : [phpied.com](http://www.phpied.com/css-coding-conventions/)


## 9. Try to use only one letter as a meaningful prefix

If it's a visual component, start with c-
If it's an object (like layout), start with o-
I just love this trick from Harry Roberts.


**Example**

```html
<button class='o-layout'>
  <div class='o-layout-item o-grid c-button'></div>
  <!-- When scanning HTML, the eye can quickly differentiate who does what-->
</button>
```


**Source** : [Harry Roberts](http://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/)

## 10. Try [] when too many classes of a kind

This little trick allows you to scan HTML quicker.
Notice the classes .[ and .] do not exists in your CSS files, it is only here to help others to read your HTML.


**Example**

```html
<button class='[ o-layout ]'>
  <div class='[ o-layout-item o-layout-item--first ] c-button'></div>
  <!-- When scanning HTML, the eye can quickly differentiate who does what-->
</button>
```


**Source** : [Source code of Inuit Kitchen Sink](https://raw.githubusercontent.com/csshugs/inuit-kitchen-sink/v0.4.0/layout.html)



## 11. Use a js- prefix if it is only used by JavaScript

If Javascript needs to target an element, don't make it rely on CSS style.
Give a dedicated prefix, like js-.

**Example**

```html
<button class='js-click-me'>
  <!-- When scanning HTML, I understand that this button has no CSS selector to design it.
       But, JavaScript will use it, probably to catch some event.-->
</button>
```

**Source :** [Derick Bailey, marion
netteJS book](https://leanpub.com/marionette-gentle-introduction)




## 12. Try to separate parent from children

If a class has to many responsibilities, split it into 2 separated properties.


**Example**

(bad)

```html
<button class='a'>
  <!-- This class below will contain a mix of properties
       some concerned by a-b relationship
       some concerned by b-c relationship
       CSS file is going to be hard to read-->
  <div class='child-of-a-and-parent-of-c'>
    <div class='c'>
    </div>
  </div>
</button>
```

(good)

```html
<button class='a'>
  <!-- Split into 2 classes-->
  <div class='child-of-a parent-of-c'>
    <div class='c'>
    </div>
  </div>
</button>
```




## 13. Unsemantic classes should explicitly describe their properties

Most of them contain only one property, there are no value in hiding what that is.

```css

.horizontal-alignment { /* Don't do this. Horizontal alignment can be achieved in many ways, when scanning this selector in HTML file, we have no clue about HOW it is achieved. */
  text-align: center;
}
/* Prefer this one. Using BEM, and a one-character prefix, see above */
.u-text-align--center {
  text-align: center;
}
```



## 14. Explicit hacks (I)


If you're not happy with your CSS selector, say it to everybody.

It will happen anyway, even to the best CSSuper(wo)men, so don't be ashamed of it.

In your team, find a word that will be used for such cases, document it, and stick to it all along the lifetime of your project.

For us, Atom IDE automatically highlight the word "HACK" so I used it.

**Example**

```css

.my-component {
  margin-left: -7px; /* HACK here : magic number, here to compensate gutter */
}

```

## 15. Explicit hacks (II)

Another valuable option is to put every weird code into a dedicated file, named **shame.css**

Again, Harry Roberts come to the rescue.

**Source :** [Harry Roberts](http://csswizardry.com/2013/04/shame-css/)




## 16. Try to avoid more than two words for a given name

The name must be self-descriptive in one or two words, or code will be hard to maintain.

**Example**

```css
.button {
  /* OK */
}
.dropdown-button {
  /* still OK */
}
.dropdown-button-part-one {
  /* Hmm, still ok, but will be unredable when adding children, for ex : */
}
.dropdown-button-part-one__button-admin {
  /* Yikes !!! */
}
```

## 17. Use data-state attribute to specify state of your component

State manipulation happens very often.
It happens so frequently that give the state a dedicated attribute saves times and effort over the long term.

**Example**

```html
<button class='c-button c-button--warning is-active'>
  <!-- Don't do this-->
</button>
<button class='c-button c-button--warning' data-state='is-active'>
  <!-- That's better.
  I removed a class declaration,
  it enforces the one-state-rule,
  and for those who use Sass, it makes code cleaner.-->
</button>
```


**Source :** Unfortunately, I can't remember who wrote about this, but his advice was very helpful.


## 18. Use has- or is- prefix for the state

State manipulation happens very often. (bis)
So adhere to a strict naming convention for the state will be very helpful

**Example**

```css
.activated {
  /* Don't do this.  I'm not quite sure what you are talking about ?*/
}
.is-activated {
  /* Yes, you're styling a state. */
}
```

**Source :** [Mobify code style](https://github.com/mobify/mobify-code-style/tree/master/css/class-naming-conventions#state)

## 19. Use a dash as a prefix when combining multiple state

You should do everything you can to avoid state combination.
But, when it is not possible, you can use this very helpful trick from Ben Smithett.


**Example**

```html
<button class="btn -color-red -size-large -shape-round"></button>
```

**Source :** [Ben Smithett](https://www.bensmithett.com/bem-modifiers-multiple-classes-vs-extend/)


## 20. Try single quote instead of double quote when declaring selector in HTML

It reduces noise a lot when reading the document.

**Example**

```html
<button class="c-button">
  <!-- BAD EXAMPLE : it uses " instead of '. Not a big deal on this tiny example, but when you deal with hundreds of selector in a HTML file, single quote is a better idea.-->
</button>
<button class='c-button'>
  <!-- Good !-->
</button>
```

**Source :** I learned it when I worked with the [Predicsis team](http://www.predicsis.com/team/)


## 21. Don't follow rules

I tried to give you some guidelines based on my own experience, and articles that helped me the most.

I doesn't mean everything will work for you, so my best advice is :

1) Try to improve your naming,
2) keep it consistent for a given project,
3) but avoid over-engineering.

If you don't feel comfortable, just skip it.

Enjoy !

_Special thanks to [@HugoGiraudel](https://twitter.com/HugoGiraudel), [@kaelig](https://twitter.com/kaelig), and [@gaetanbt](https://twitter.com/gaetanbt) for their reviews_
