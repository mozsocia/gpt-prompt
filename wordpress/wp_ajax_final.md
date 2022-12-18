can you teach me ajax form submission in wordpress?? using html php js with wp_ajax_{action} , `action` property  with example
Sure, here is an example of using ajax form submission in WordPress:

First, create a form in HTML with the desired fields and a submit button:

Copy code
```html
<form id="myForm">
  <input type="text" name="name" placeholder="Enter your name">
  <input type="email" name="email" placeholder="Enter your email">
  <input type="submit" value="Submit">
</form>
```
Next, add the JavaScript code to handle the ajax form submission using the wp_ajax_{action} hook and the action property:

Copy code
```js
jQuery(document).ready(function($) {
  // Handle form submission
  $('#myForm').submit(function(e) {
    e.preventDefault();
    var data = $(this).serialize();
    $.ajax({
      url: '<?php echo admin_url('admin-ajax.php') ?>',
      type: 'POST',
      data: {
        action: 'my_ajax_form_action',
        data: data
      },
      success: function(response) {
        alert(response);
      }
    });
  });
});
```
Finally, add the PHP code to handle the ajax action and process the form data:

Copy code
```php
add_action('wp_ajax_my_ajax_form_action', 'my_ajax_form_handler');
add_action('wp_ajax_nopriv_my_ajax_form_action', 'my_ajax_form_handler');

function my_ajax_form_handler() {
  // Verify the nonce
  check_ajax_referer('my_ajax_form_nonce', 'security');

  // Process the form data
  $name = sanitize_text_field($_POST['data']['name']);
  $email = sanitize_email($_POST['data']['email']);

  // Do something with the data (e.g. save to database, send email, etc.)

  // Return a response
  wp_send_json('Form submitted successfully!');
}
```
Note: In the above code, you need to replace my_ajax_form_action with your own unique action name and add a nonce field to the form for security.