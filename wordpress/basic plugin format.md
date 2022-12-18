Here is an example of a simple WordPress plugin file that you can use as a starting point for your own plugin:

Copy code
```php
<?php
/*
Plugin Name: My Plugin
Description: This is a simple plugin that does something cool.
Version: 1.0
Author: John Doe
*/

// Define the plugin directory path and URL
define('MY_PLUGIN_PATH', plugin_dir_path(__FILE__));
define('MY_PLUGIN_URL', plugin_dir_url(__FILE__));

// Register a function to be called when the plugin is activated
register_activation_hook(__FILE__, 'my_plugin_activate');

function my_plugin_activate() {
    // This function will be called when the plugin is activated
}

// Register a function to be called when the plugin is deactivated
register_deactivation_hook(__FILE__, 'my_plugin_deactivate');

function my_plugin_deactivate() {
    // This function will be called when the plugin is deactivated
}

// Register a function to be called when the plugin is uninstalled
register_uninstall_hook(__FILE__, 'my_plugin_uninstall');

function my_plugin_uninstall() {
    // This function will be called when the plugin is uninstalled
}

// Register a function to add a new menu page to the WordPress admin panel
add_action('admin_menu', 'my_plugin_menu_page');

function my_plugin_menu_page() {
    add_menu_page(
        'My Plugin Settings', // Title of the page
        'My Plugin', // Text to be used for the menu
        'manage_options', // Capability required to access the page
        'my-plugin-settings', // Unique slug for the page
        'my_plugin_settings_page', // Function that displays the content of the page
        'dashicons-admin-generic', // Icon to be used for the menu
        6 // Position of the menu in the admin panel
    );
}

function my_plugin_settings_page() {
    // This function will display the content of the plugin's settings page
}

// Register a function to add a new shortcode
add_shortcode('my_plugin', 'my_plugin_shortcode');

function my_plugin_shortcode($atts) {
    // This function will be called when the shortcode is used
}
```