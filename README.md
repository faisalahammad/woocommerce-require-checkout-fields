# WooCommerce Require Checkout Fields

WooCommerce checkout fields not customizable from WooCommerce settings page. But sometimes you need to make some fields require or optional. So where from you could make those fields require or optional? Hmmm, tricky question!

First you've to know how to create child theme so we could override our parent theme. Check the codex page and create your <a href="https://codex.wordpress.org/Child_Themes" target="_blank">Child Theme</a>. Then go to `functions.php` and add below codes.

I'd like to make require <strong>Address, City, State & Zip code</strong> so I'm going to add those code. 

```php
function your_require_wc_multiple_fields( $fields ) {
    $fields['address_1']['required'] = $fields['city']['required'] = $fields['state']['required'] = $fields['postcode']['required'] = true;
    return $fields;
}
add_filter( 'woocommerce_default_address_fields', 'your_require_wc_multiple_fields' );
```

But if you'd like to make optional then use `false` instade of `true`. Also if you'd like to make require/optional two or more then use `=` sign.

#### Example
```php
$fields['city']['required'] = true / false; // Single action
$fields['address_1']['required'] = $fields['city']['required'] = true / false; // Multiple Action
```

<strong>You will get more information about Customize WooCommerce Checkout fields using Action & Filter hooks on <a href="https://docs.woocommerce.com/document/tutorial-customising-checkout-fields-using-actions-and-filters/">WooCommerce Documentation</a> page.</strong>