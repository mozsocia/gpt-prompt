can you teach me how to use form input in wordpress custom plugin 
Sure, I'd be happy to help you with that. To use form inputs in a WordPress custom plugin, you'll need to create a custom plugin and add a form to it. Here's an overview of the steps you can follow to do this:

Create a new folder in the wp-content/plugins directory of your WordPress installation, and give it a name that reflects the purpose of your plugin.

In the plugin folder, create a new PHP file and name it pluginname.php, where pluginname is the name you gave to your plugin folder. This file will contain the main code for your plugin.

In the pluginname.php file, add the following code at the top to create the plugin header:

Copy code
```php
<?php
/*
Plugin Name: Plugin Name
Description: A brief description of the plugin
Version: 1.0
Author: Your Name
*/
```
To add a form to your plugin, you can use the add_menu_page function to create a new top-level menu item in the WordPress admin panel, and then use the add_submenu_page function to create a submenu page that will contain your form. For example:
Copy code
```php
function pluginname_add_menu_page() {
    add_menu_page(
        'Plugin Name', // Page title
        'Plugin Name', // Menu title
        'manage_options', // Capability
        'pluginname', // Menu slug
        'pluginname_display_form', // Function to display the form
        'dashicons-admin-generic', // Icon URL
        6 // Menu position
    );
}
add_action( 'admin_menu', 'pluginname_add_menu_page' );

function pluginname_add_submenu_page() {
    add_submenu_page(
        'pluginname', // Parent slug
        'Form', // Page title
        'Form', // Menu title
        'manage_options', // Capability
        'pluginname-form', // Menu slug
        'pluginname_display_form' // Function to display the form
    );
}
add_action( 'admin_menu', 'pluginname_add_submenu_page' );
```
Next, you'll need to create the pluginname_display_form function that will be called to display the form. This function should print the HTML for the form, including the form inputs and any other elements you want to include. For example:
Copy code
```php
function pluginname_display_form() {
    // Check user capabilities
    if ( ! current_user_can( 'manage_options' ) ) {
        return;
    }

    // Form HTML
    ?>
    <div class="wrap">
        <h1>Form</h1>
        <form method="post" action="">
            <table class="form-table">
                <tr>
                    <th scope="row">
                        <label for="input1">Input 1</label>
                    </th
