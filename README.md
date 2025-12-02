WordPress Theme Customization Examples (PHP Snippets)

This repository contains sample PHP snippets demonstrating my ability to edit and extend WordPress themes, specifically through dynamic elements commonly added to footer.php, functions.php, or custom plugin files.

These examples reflect real-world edits made for client sites in industries such as healthcare, e-commerce, and professional services. The goal is to illustrate practical working knowledge of PHP within WordPress theme architecture.

Features Demonstrated:

 - Injecting PHP inside HTML templates

 - Using WordPress core functions (wp_get_recent_posts, get_permalink, esc_html)

 - Adding dynamic content (e.g., current year, latest blog post)

 - Creating maintainable, theme-safe customizations

1. Dynamic Footer: Display Current Year

This example shows how PHP can be embedded inside HTML to automatically update the copyright year.

Simple PHP Integration:

<footer>
    <p>&copy; <?php echo date('Y'); ?> YourCompanyName. All rights reserved.</p>
</footer>

2. Dynamic Footer: Display Most Recent Blog Post

This snippet can be placed inside a theme file, such as footer.php, to pull and display the latest published WordPress blog post as follows:

<footer>
    <p>&copy; <?php echo date('Y'); ?> YourCompanyName. All rights reserved.</p>

    <?php
    $recent_post = wp_get_recent_posts(array('numberposts' => 1));
    if (!empty($recent_post)) {
        $post = $recent_post[0];
        echo '<p>Latest post: <a href="' . get_permalink($post['ID']) . '">' 
            . esc_html($post['post_title']) . '</a></p>';
    }
    ?>
</footer>

3. Hook-Based Version (functions.php)

For theme-safe, reusable functionality, this version hooks into the wp_footer action instead of editing template files directly.

<?php
function mytheme_latest_post_footer() {
    $recent_post = wp_get_recent_posts(array('numberposts' => 1));
    if (!empty($recent_post)) {
        $post = $recent_post[0];
        echo '<p>Latest post: <a href="' . get_permalink($post['ID']) . '">'
            . esc_html($post['post_title']) . '</a></p>';
    }
}
add_action('wp_footer', 'mytheme_latest_post_footer');

<?php
function mytheme_year_in_footer() {
    echo '<p>&copy; ' . date('Y') . ' YourCompanyName. All rights reserved.</p>';
}
add_action('wp_footer', 'mytheme_year_in_footer');
