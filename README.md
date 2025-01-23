# Redirect Non-Logged-In Users to Google for a Specific LearnDash Course

This snippet redirects visitors who are not logged in to WordPress to another link when they attempt to access a specific LearnDash course.

## Usage

### Prerequisites
- LearnDash LMS installed and running on your WordPress site.
- A specific course ID that you want to target for the redirection.

### Installation

1. Copy the snippet code below:
<?php
/**
 * Redirect non-logged-in users only to another link for a specific course ID.
 */
add_action( 'template_redirect', function() {
    // Specify the course ID for which the redirection should occur.
    $target_course_id = 123; // Replace 123 with your specific course ID.

    // Check if the current user is not logged in and if the course ID matches.
    if ( ! is_user_logged_in() && is_singular( 'sfwd-courses' ) && get_the_ID() === $target_course_id ) {
        // Replace the https://www.google.com for the redirection
        wp_redirect( 'https://www.google.com' );
        exit; 
    }
} );
    ```
2. Paste the code into one of the following:
    - Your theme's `functions.php` file.
    - A custom plugin file.

3. Replace the `123` in `$target_course_id` with the ID of the specific course you want to target.

### How It Works

1. **Course Check**: The code identifies if the current page is a LearnDash course (`sfwd-courses`) and matches the specified course ID.
2. **Login Check**: It verifies if the visitor is not logged in to WordPress.
3. **Redirection**: If both conditions are met, the visitor is redirected to another link.

### Example

If the course ID is `456`, update the snippet like this:
```php
$target_course_id = 456;
