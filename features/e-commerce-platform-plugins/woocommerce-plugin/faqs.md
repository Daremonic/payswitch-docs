---
description: Quick answers to commonly asked questions about PaySwitcher
---

# FAQs

{% hint style="info" %}
This section covers the frequently asked questions you might have around PaySwitcher product, features, payment process, PCI compliance, woocommerce, etc.\
We regularly update the common questions here.
{% endhint %}

**Is my customer information shared with other plugin users?**

No. PaySwitcher Woocommerce plugin does not share customer data across other plugin users. Yours customer’s cards will be stored in a PCI compliant card vault powered by [PaySwitcher](https://payswitcher.com/)\\

**What will happen to my customers’ saved cards, if I move out of PaySwitcher?**

If for any reason you happen to move out of PaySwitcher, you will be facilitated with the process of migrating the cards to any PCI compliant entity as you might wish.\\

**Who built and maintains the plugin?**

The plugin is built and maintained by PaySwitcher Inc. - a leading payment orchestrator.\\

**How can I customize the payment sheet as per my branding?**

The plugin ensures that the payment sheet automatically blends into the website’s theme by fetching the basic style attributes from the page. However, attributes of the payment sheet such as font family, text and background color etc can be customized by modifying the _“Appearance”_ object present in the Payment settings.\\

**Are my other plugins compatible with the PaySwitcher plugin?**

Yes, this plugin can be used along with other payment plugins. However, we would advise **not** to use other payment plugins for better customer experience.\\

**How will I receive chargeback notifications?**

This feature is currently being developed by PaySwitcher where any chargeback/refund notifications would be sent via Webhooks to your Wordpress server, which would then update the order status accordingly. Provided that Webhooks are enabled and Payment Response Hash Key is correctly configured, you would be able to receive these notifications realtime.\\

**How do I cancel orders and trigger refunds with the PaySwitcher plugin?**

Orders can be refunded from the Orders Management section of your WP Admin dashboard. The order status is automatically updated to _“Refunded”._\\

**Does the PaySwitcher plugin support multiple languages?**

Currently, en-US is the only supported language.\\

**How much will PaySwitcher charge me for using the plugin?**

3k transactions monthly are free forever if you sign-up prior to 30th Nov 2023. $0.03/ successful transaction otherwise or if the 3k limit is crossed. Find out more on pricing [here](https://payswitcher.com/pricing).\\

**How do I enable/ disable payment methods on the plugin?**

Different payment methods across Payment Processors can be enabled/disabled on the PaySwitcher Dashboard.\\

**Are my other plugins compatible with PaySwitcher plugin?**

WooCommerce is not explicitly built to handle embedded checkouts so we had to build support for this in our plugin. Different extensions implement/expand the functionality in slightly different ways and there is always a small risk that compatibility problems may arise.

Our ambition is always that our plugins should be compatible with as many functions and extensions as possible. We work actively with this and release regular updates that lead to a better experience, both for you as an e-retailer but also for your customers.

Please feel free to drop a request to biz@payswitcher.com with the name of the plugin for which you need compatibility.
