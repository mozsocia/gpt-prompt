In WordPress, user roles are used to control access to different parts of the website. To check a user's role, you can use the get_userdata() function to retrieve the user's information, and then check the roles property of the resulting WP_User object. Here's an example:

Copy code
```php
$user = get_userdata( $user_id );
if ( ! empty( $user->roles ) && is_array( $user->roles ) ) {
    // Loop through the user's roles
    foreach ( $user->roles as $role ) {
        echo $role; // Print the user's role
    }
}
```
In this example, $user_id is the ID of the user whose role you want to check. You can replace this with a specific user ID, or use a function like get_current_user_id() to get the ID of the currently logged-in user.

Keep in mind that a user can have multiple roles, so the $user->roles property will be an array of roles. The code above will loop through each role and print it to the screen. You can modify this code to perform different actions based on the user's role, such as redirecting the user to a different page or showing/hiding certain content.

I hope this helps! Let me know if you have any other questions.