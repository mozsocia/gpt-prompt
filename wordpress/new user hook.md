wp action hook to fire when a new user is created

In WordPress, an action hook is a specific point in the WordPress codebase where developers can add their own custom code. One action hook that fires when a new user is created is the user_register action hook.

Here's an example of how you can use the user_register action hook to perform a custom action when a new user is created:

Copy code
```php
function custom_action_on_user_registration( $user_id ) {
    // Perform your custom action here
}
add_action( 'user_register', 'custom_action_on_user_registration' );
```
In this example, the custom_action_on_user_registration function will be executed whenever a new user is created. The user's ID is passed as an argument to the function, so you can use it to access information about the user or perform other actions specific to that user.

It's also possible to use the wp_insert_user action hook to perform an action when a new user is created. This hook fires just before a user is inserted into the database, so it can be used to modify user data before it is saved.

Copy code
```php
function custom_action_on_user_creation( $user_data ) {
    // Perform your custom action here
}
add_action( 'wp_insert_user', 'custom_action_on_user_creation' );
```
In this example, the custom_action_on_user_creation function will be executed just before a new user is inserted into the database. The user data is passed as an argument to the function, so you can use it to modify the user data before it is saved.