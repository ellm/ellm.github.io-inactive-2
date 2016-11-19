---
layout: page
title: Php
permalink: /notes/php
---

# Comparing isset() and empty()

I've encountered many notices in PHP that are generally solved by first checking to see if a variable contains a value. This is a good practice to begin with but sometimes it slips through the cracks. Two methods that PHP has to check a value are `isset()` and `empty()`. Both of these methods is that they return a boolean value.. I was confused by the difference in these two methods, so I am going to try to explain them here. `isset()` - Returns true if a variable is set and is not NULL

```php
// Example 1
$var = '';

// This will evaluate to TRUE so the text will be printed.
if (isset($var)) {
echo "This var is set so I will print.";
}

```

* * *

`empty()` - Returns true if a variable is empty - A variable is considered empty if it does not exist or if its value equals FALSE. The following things are considered to be empty: - "" (an empty string) - 0 (0 as an integer) - 0.0 (0 as a float) - "0" (0 as a string) - NULL - FALSE - array() (an empty array) - $var; (a variable declared, but without a value)

```php
$var = 0;

// Evaluates to true because $var is empty
if (empty($var)) {
echo '$var is either 0, empty, or not set at all';
}

// Evaluates as true because $var is set
if (isset($var)) {
echo '$var is set even though it is empty';
}

```

----

### Type Casting

`(String)$var` - converts a variable to a string

### Echo a multi-line HTML block

```php
echo <<< EOT
    <aside class="phone widget">
        <h1 class="widget-title screen-reader-text">Call Wilf Campus</h1>

<div class="phone">

## **Register Now For Webinar**

        </div>

    </aside>
EOT;
```

### Useful Built-in Functions

[Php Built-In Function Reference Link](http://php.net/manual/en/funcref.php) `printf` - can be used to output HTML

```php
printf('<div class="mre_test_wrap">%s</div>', 'This is a string'); // String

printf('<div class="mre_test_wrap">%u</div>', '6');//Number

//Example using multiple parameters
printf( __( 'Posted on <a href="%1$s" title="%2$s" rel="bookmark"><time class="entry-date" datetime="%3$s" pubdate>%4$s</time></a>', 'wp_arch' ),
    esc_url( get_permalink() ),
    esc_attr( get_the_time() ),
    esc_attr( get_the_date( 'c' ) ),
    esc_html( get_the_date() )
);

// Another example using multiple parameters
printf('<div class="col-img">![%s](%s)</div>', $itc_partner_graphic, $itc_partner_name);</pre>

```

*   strip_tags()
*   sort()/rsort()
*   floor()

----

### PHP Lambdas, Closures and Anonymous Functions

"Lambdas are useful because they are throw away functions that you can use once. Often, you will need a function to do a job, but it doesn’t make sense to have it within the global scope or to even make it available as part of your code. Instead of having a function used once and then left lying around, you can use a Lambda instead."

```php
$mre_lambda_pubdate = function () use ($wpdb) {
    $originalDate = $wpdb->get_var("SELECT post_modified FROM {$wpdb->posts} WHERE ID = 31");
    $newDate = date("F j, Y g:i a", strtotime($originalDate));
    return '<p>Last Updated: <strong><time>' . $newDate . '</time></strong></p>';
};
echo $mre_lambda_pubdate();
```

Resources: [http://culttt.com/2013/03/25/what-are-php-lambdas-and-closures/](http://culttt.com/2013/03/25/what-are-php-lambdas-and-closures/) [http://php.net/functions.anonymous](http://php.net/functions.anonymous)

----

# Debugging Wordpress

### Enable Debugging

Open `wp-config.php` and add the following:

```php
define( 'WP_DEBUG', true );

```

Use <span class="lang:default decode:true  crayon-inline ">var_dump(expression)</span> or <span class="lang:default decode:true  crayon-inline ">print_r(expression);</span> debugging to inspect variables:

```php
var_dump($var);
die(); // stops parsing after this point

```

Super Global Variable for Debugging

*   available in all scopes
*   stored as a associative array

```php
$_SERVER; //information about the web server environment

print_r($_GET) // information on get request header
print_r($_GET['id']) // information on get request header 'id'

```

### View PHP Error Logs

_Using Varying-Vagrant-Vagrants_

```
sudo tail -f /srv/log/php_errors.log
```

### More In Depth Debugging? Use xDebug

_Using Varying-Vagrant-Vagrants_ In the terminal: - Turn on xDebug: `xdebug_on` - Turn off xDebug: `xdebug_off` - Restart php5-fpm: `sudo service php5-fpm restart`

### Example Error Messages

1.  Unexpected End - usually a missing curly brace
2.  Undefined Index - Can not find index in array (look our for case sensitivity)

``` php
// Undefined Index
$query_age = (isset($_GET['query_age']) ? $_GET['query_age'] : null);
// http://stackoverflow.com/questions/4842759/php-undefined-index

```

### Other Tools

#### WordPress Code Standards - Php Code Sniffer

This project is a collection of PHP_CodeSniffer rules (sniffs) to validate code developed for WordPress. It ensures code quality and adherence to coding conventions, especially the official WordPress Coding Standards. Resources below for installation

*   [PHPCS WordPress Code Standards](https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards)
*   [Sublime Linter PHPCS](https://github.com/SublimeLinter/SublimeLinter-phpcs)
*   [Tutorial on Installing PEAR on OSX](http://jason.pureconcepts.net/2012/10/install-pear-pecl-mac-os-x/)
*   [PEAR Installation Docs](http://pear.php.net/manual/en/installation.getting.php)
*   [Php-codesniffer installation](http://pear.php.net/manual/en/package.php.php-codesniffer.php)

### References

*   [VVV Code Debugging](https://github.com/Varying-Vagrant-Vagrants/VVV/wiki/Code-Debugging)

***

# PHP Control Structures and Loops

### Explicit Boolean Values

*   keywords: true and false
*   Case-insensitve
    *   `$OK = TRUE`;
    *   `$OK = FaLsE`;

### Implicit Boolean Values

PHP regards the following values as false:

*   False and Null
*   Zero as a number or string (0, 0.0, '0')
*   An Empty string ('', "")
*   An Empty array

### Comparison Ops

== (equals) === (identical)

### Switch Statement

*   an alternative to if/else; sometimes easier to maintain
```php
switch ($variable) {
    case 'value':
        # code...
        break;
    // case for two vars
    case 'value':
    case 'value':
        # code...
        break;
    default:
        # code...
        break;
}
```

### Ternary Operator

`$var = (condition) ? value_if_true : value_if_false;`

### Style Guidlines Tips

See DeMorgan's laws to simplify boolean expressions

#### Avoid Empty if-parts

``` php
// Example A - INCORRECT:
if (is_page()) {
    // do nothing
} else {
    echo "hello";
}
// Example B - CORRECT:
if (!is_page()) {
    echo "hello";
}
```

#### Don't Use true or false in conditions

```php
// Example A - INCORRECT:
if (is_page() == true) {
    // do something
}

// Example B - CORRECT:
if ( is_page() ) {
    // do something
}
```

***

# PHP Mail Functions

## GET and POST

*   Good rules
*   GET method should only be used for search forms because form values are exposed in the URL
*   POST method for sending email or inserting records into a database

## Unwanted backslashes

*   'Magic Quotes' function enabled on servers will add 'backslashes' to GET and POST array values
*   Set to be deprecated
*   Make sure they are OFF on all server environments ( check phpinfo() )
*   Can be turned off using .htaccess

## How PHP Sends mail

*   mail() function
*   5th arg optional (to prevent a 'X-Warning' header from being added to the message when the envelope sender (-f) is set using this method. For sendmail users, this file is /etc/mail/trusted-users.)

## Mail Catcher

*   Use MailCatcher (installed on VVV) to preview how email is sent; Good for debugging

***

### Classes

PHP is not an object oriented language. But it does have considerable support for object oriented programming. Example:

```php
$now = new DateTime();
echo $now->format('F j, Y h:ia');
```

### Sharing a variable between functions in a class

Example:

``` php
if ( ! class_exists( 'MyClass' ) ) {
    class MyClass {
        // Variable is visible in all classes that extend current class (including the parent class).
        // Defines variable constant
        protected $_foo;

        public function __construct($foo = '') {
            // Setting the constant variable to local variable
            $this->_foo = $foo;
            $this->bar();
        }

        function bar () {
            $output = $this->_foo;
           return $output;
        }

    }
    new MyClass;
}
```

#### Resources:

*   [http://stackoverflow.com/questions/19016696/passing-variable-between-functions-php#answer-19016830](http://stackoverflow.com/questions/19016696/passing-variable-between-functions-php#answer-19016830)
*   [http://stackoverflow.com/questions/13530465/how-to-declare-a-global-variable-in-php](http://stackoverflow.com/questions/13530465/how-to-declare-a-global-variable-in-php)

### Objects

Example of returning a member variable of an Object:

`$obj->scalar;`
