---
layout: collection_item
title:  "Wordpress Notes"
category: wordpress
tags: php, backend, wordpress
---

# Wordpress learning
## What tools to use?
**Answer:** 
* Flywheel
    * live preview with ngrok server for free
    * it configures everything for me automatically so I don't have configure anything manually.
    * Very fast setup and easy to use.
    
## How to create a new theme in wordpress?
**Answer**:
* Reveal wordpress project in a folder.
* Go to app>public>wp-content>themes.
* Create a new folder. The naming convention should look like this.
  "my-theme"
* Create an index.php, style.css.
* Add the following comment in your style.css **[important]**
  ```css
  /*
      Theme name: My Theme
      Author: Prince Billy Graham
      Version: 1.0
   */
  ```
  *Except the theme name, all other parameters are optional here.*
* (Optional) Add a new image in the same folder named "screenshot.jpeg" which has to be a dimension of 1200x900px

## `blogInfo()` function
`blocgInfo()` is a prebuild function in wordpress. and can give us specific information.
[more...](https://developer.wordpress.org/reference/functions/bloginfo/)
```phpregexp
blogInfo('name') //prints the wordpress site description
blogInfo('description') //prints the wordpress site tagline
```

## How to work with wordpress classic editor?
* Go to Add new Plugin
* Search for "Classic Editor" by wordpress and install it.
* Activate the plugin and from now on you will see the classic editor instead of the new block editor



## The Famous loop (The loop)

This is a special kind of loop which is commonly used for adding content to pages.
```php
<?php while(have_posts()) { the_post(); ?>
<a href="<?php the_permalink(); ?>" >
    <h1><?php the_title(); ?></h1>
</a>
    <p><?php the_content(); ?></p>
<? } ?>
```
**Note**: The same format will be used even if thier is only one content.

## What page in theme folder wordpress uses for what purpose?
* `index.php` -> home page
* `single.php` -> post page
* `page.php` -> general pages

## Adding Header and footer in theme
* We can create a separate file named `header.php`
where we can keep our header.
   ```php
  <!doctype html>
  <html lang="en">
  <head>
    <?php wp_head(); ?>
  </head>
  <body>
  ```
**Notes:** Here `wp_head()` function is necessary to add default wordpress header.

* We can also create a footer using a file named `footer.php`.
  ```php
  <?php wp_footer(); ?>
  </body>
  </html>
  ```
* To add this to a specific page like `index.php`, `post.php` and `pages.php` we need to call two specific functions
  * `get_header();` --> Adds the contents of `header.php` to the page
  * `get_footer();` --> Adds the contents of `footer.php` to the page

* We can also add custom styles to wordpress using wordpress hooks. For that we need to create a new php file named  `functions.php` and write the following codes:

```php
<?php
function add_my_custom_style() {
    wp_enqueue_style('my_custom_style', get_stylesheet_uri());
}

add_action('wp_enqueue_scripts', 'add_my_custom_style');
```

  
 
