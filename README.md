# WooCommerce Subscriptions Upstage

Using [WooCommerce Subscriptions](https://woocommerce.com/products/woocommerce-subscriptions/)? Need to test automatic payments on a staging site?

By default, when WooCommerce Subscriptions detects a change in a site's URL, it switches to [_Staging Mode_](https://docs.woocommerce.com/document/subscriptions-handles-staging-sites/). In _Staging Mode_, all subscriptions are forced to use manual renewals. This prevents accidental, duplicate renewal payments being processed by staging sites.

On occasion, there is a need to process automatic payments on staging sites, generally for testing.

This plugin can be used to trigger automatic payments for specific subscriptions when Subscriptions is in _Staging Mode_.

## Usage

1. Download the [latest version of the plugin](https://github.com/Prospress/woocommerce-subscriptions-upstage/archive/master.zip)
1. [Install & activate](https://codex.wordpress.org/Managing_Plugins#Installing_Plugins) the plugin
1. Define a `WCS_UPSTAGED_SUBSCRIPTION_IDS` constant
1. Set its value to an array of subscription IDs (`int`'s)

[Automatic renewal payments](https://docs.woocommerce.com/document/subscriptions/renewal-process/) will then be triggered for those subscription IDs.

### Example Usage

```
define( 'WCS_UPSTAGED_SUBSCRIPTION_IDS', json_encode( array( 123, 5813, 2134 ) ) );
```

### Suggested Usage

While the `WCS_UPSTAGED_SUBSCRIPTION_IDS` constant can be defined anywhere, your site's [`wp-config.php`](https://codex.wordpress.org/Editing_wp-config.php) file is often the best place for defining this type of constant.

## Requirements

The plugin will only trigger automatic payments when:

* the site is in [_Staging Mode_](https://docs.woocommerce.com/document/subscriptions-handles-staging-sites/), it does nothing when the site is in _Live Mode_
* a `WCS_UPSTAGED_SUBSCRIPTION_IDS` constant is defined
* the `WCS_UPSTAGED_SUBSCRIPTION_IDS` constant is an array

If those conditions are met, when a scheduled renewal event occurs for a subscription in the `WCS_UPSTAGED_SUBSCRIPTION_IDS` array, this plugin will trigger the [automatic renewal payment](https://docs.woocommerce.com/document/subscriptions/renewal-process/) process.

## Reporting Issues

If you find an problem or would like to request this plugin be extended, please [open a new Issue](https://github.com/Prospress/woocommerce-subscriptions-upstage/issues/new).

---

<p align="center">
	<a href="https://prospress.com/">
		<img src="https://cloud.githubusercontent.com/assets/235523/11986380/bb6a0958-a983-11e5-8e9b-b9781d37c64a.png" width="160">
	</a>
</p>