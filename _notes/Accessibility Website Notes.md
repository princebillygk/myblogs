---
layout: collection_item
title:  "Accessibility of a website"
category: Web Development
tags: accessibility website
---

### Catagories of imparement
* Visual
* Motor
* Hearing
* Cognitive

### Duration of imparement
* Temporary
* Permanent
* Situational

## WCAG  (POUR)
* Perceivable 
* Operable
* Understandable
* Robust

## Website where we can find the guidline:
1. [WebAIM's WCAG 2 Checklist](https://webaim.org/standards/wcag/checklist)
2. 

## Focus
Tab -> Focus to next component
Shift + Tab -> Focus to previous component
Arrows -> Move inside a component

Tips:
* Keep the order of dom in your html relevent to the actuall position of it in the webpage which can be customized by CSS

* Use `tabindex` attribute to manage focus
`tabindex=0` -> means focus it and include it in tabindex. `tabindex=-1` means not included in tabindex. `tabindex` greater than 0 is not recommnended.
* Use skip links to main content and other item according to our needs
* Modal keyboard trap must be implemented

Semeantics
* Use the semantics tags provided by html
* Use proper `alt` attribute for image element if you want the screen reader to completely avoid an image them add an empty valued `alt` tag. (eg. `alt=""`)
* Don't forget to add label to input field using for keyword

# Styling
* Use the `::focus`` sudo class to change the styling of the outline and the element when it is focused
* Use aria attribute rather than css class name for styling
* Use <meta name="viewport" content="width=device-width, intial-scale=1>
* Font size `em` -> relatvie to parent item, `rem` -> relative to root item
* On mobile or touch devices the minimum size of a clickable element should be atleast 48px x 48px so it is easily touchable
* Adjust the contrast ratio and detecting it using a tool (Chrome accessibility dev tool)focusable 
* If try to indicate a message with color also add aditional text for the color blind users.
* Enable high constrast extension and see if everything looks ok

