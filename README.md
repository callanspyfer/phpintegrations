WordPress Theme Customization Examples (PHP Snippets)

This repository contains sample PHP snippets demonstrating steps towards enhancing WordPress themes, specifically through dynamic elements commonly added to footer.php, functions.php, or custom plugin files.

These examples reflect real-world edits made for client sites in industries such as healthcare, e-commerce, and professional services. This repository aims to improve working knowledge of PHP and assist in the implementaion of integrating PHP for dyanmic elements within the WordPress theme architecture that enhance the user experience and retention, leading to more conversions.

Features Demonstrated:

 - Injecting PHP inside HTML templates

 - Using WordPress core functions (wp_get_recent_posts, get_permalink, esc_html)

 - Adding dynamic content (e.g., current year, latest blog post)

 - Creating maintainable, theme-safe customizations

Dynamic Footer: Display Current Year

This example shows how PHP can be embedded inside HTML to automatically update the copyright year.

Simple PHP Integration:

 ```php

<?php echo date('Y'); ?>

```


<footer>
 
 <p>&copy;  <?php echo date('Y'); ?> YourCompanyName. Year. All rights reserved.

 <footer>

Dynamic Footer: Display Most Recent Blog Post

This snippet can be placed inside a theme file, such as footer.php, to pull and display the latest published WordPress blog post as follows:

<footer>
    <p>&copy; <?php echo date('Y'); ?> YourCompanyName. Year. All rights reserved.</p>

    <?php
    $recent_post = wp_get_recent_posts(array('numberposts' => 1));
    if (!empty($recent_post)) {
        $post = $recent_post[0];
        echo '<p>Latest post: <a href="' . get_permalink($post['ID']) . '">' 
            . esc_html($post['post_title']) . '</a></p>';
    }
    ?>
</footer>

