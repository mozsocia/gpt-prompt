how to add new custom column  from database in wordpress all users menu php 

To add a new custom column to the WordPress all users menu, you will need to follow these steps:

Open the functions.php file in your theme or plugin.

Add the following code to register a new column in the all users menu:
```php
function add_custom_column($columns) {
$columns['custom_column'] = 'Custom Column';
return $columns;
}
add_filter('manage_users_columns', 'add_custom_column');
```

Next, you will need to add the code to display the custom column data for each user. To do this, you will need to use the "manage_users_custom_column" filter:

```php
function display_custom_column($value, $column_name, $user_id) {
if ($column_name == 'custom_column') {
// Retrieve the custom data from the database
$custom_data = get_user_meta($user_id, 'custom_data', true);
return $custom_data;
}
return $value;
}
add_filter('manage_users_custom_column', 'display_custom_column', 10, 3);
```
Finally, you will need to update the database to store the custom data for each user. To do this, you will need to use the "update_user_meta" function:

```php

update_user_meta($user_id, 'custom_data', 'Your custom data here');

```
Once you have added the above code to your functions.php file, your custom column should now be displayed in the all users menu.