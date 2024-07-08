---
description: WooCommerce Plugin Setup
---

# Setup

{% hint style="info" %}
This section covers the steps to setup woocommerce plugin on your website and managing the orders from the dashboard.
{% endhint %}

### Prerequisites

1. Sign up on the PaySwitcher dashboard and navigate to connectors tab [here](https://app.payswitcher.com/) to configure connector(s) and enable various Payment Methods.
2. WooCommerce plugin must be installed and enabled on your WordPress website. Visit [here](https://wordpress.org/plugins/woocommerce/) or go to your WordPress Admin dashboard and navigate to "Plugins" section to install and enable the WooCommerce Plugin.

### 1. Setting up the Plugin on your Website

#### 1.1 Download the Plugin

#### 1.2 Installing the Plugin

Head to your WordPress Admin Dashboard, and navigate to Plugins > Add New

<figure><img src="https://payswitcher.com/img/site/wordpress_plugins.png" alt=""><figcaption></figcaption></figure>

Click on "Upload Plugin". Click on "Choose File" and browse to the directory where you downloaded the plugin file (payswitcher-checkout.zip) in 1.1, and select it, complete the installation and activate the plugin.

<figure><img src="https://payswitcher.com/img/site/wordpress_addplugin.png" alt=""><figcaption></figcaption></figure>

#### 1.3 Configuring the Plugin

Navigate to Woocommerce > Settings section in the dashboard. Click on the "Payments" tab and you should be able to find PaySwitcher listed in the Payment Methods table.

<figure><img src="https://payswitcher.com/img/site/wordpress_settings.png" alt=""><figcaption></figcaption></figure>

Click on "Pay via PaySwitcher" to land on the PaySwitcher Plugin Settings page. Configure your PaySwitcher credentials here, including the Environment, Secret Key, Publishable Key, and Payment Response Hash Key to establish a secure connection between your website and PaySwitcher. You can find these keys in the "Developers" section of your [PaySwitcher dashboard](https://app.payswitcher.com/developers).

Configure various Payment Controls, such as Capture Method, Webhooks and Saved Customer Payment Methods when PaySwitcher is selected during checkout.

This plugin is built to seamlessly tailor the payment experience to match your website's branding by blending the payment form into your WordPress theme. You can further customize the "Appearance" and "Layout" of the payment form using styles or pre-built themes. Read more about customization [here](https://payswitcher.com/docs/sdkIntegrations/unifiedCheckoutWeb/customization).

<figure><img src="https://payswitcher.com/img/site/wordpress_payswitcher_settings.png" alt=""><figcaption></figcaption></figure>

**Note:** To receive webhooks, ensure that you copy the Webhook URL displayed under the "Enable PaySwitcher Webhook" checkbox and paste it onto the "Webhook URL" text field in the Developers > Webhooks section of your [PaySwitcher dashboard](https://app.payswitcher.com/developers).

### 2. Orders Management on WooCommerce Dashboard

With the PaySwitcher plugin seamlessly integrated into your WooCommerce Dashboard, you gain powerful order management capabilities to enhance your e-commerce operations. This plugin provides access to features that PaySwitcher brings to your WooCommerce order management, enabling you to capture payments manually, create refunds, sync payment status, and update orders via webhooks.

#### 2.1 Manual Payment Capture:

You can choose to capture customer payments automatically or manually, as per your needs. If you wish to exercise the latter option, all you need to do is to update the "Capture Method" in the PaySwitcher Plugin settings to "Manual".

Once a customer authorizes their payment, you can easily capture payments manually through the Woocommerce Dashboard. Navigate to the Order Details page and click on the "Order Actions" dropdown. Select the "Capture Payment with PaySwitcher" option, and click on "Update".

<figure><img src="https://payswitcher.com/img/site/wordpress_manual_capture.png" alt=""><figcaption></figcaption></figure>

PaySwitcher will process the payment, update the payment status, and provide you with real-time payment details.

#### 2.2 Refunds:

In cases where you need to issue a refund to a customer, the PaySwitcher plugin streamlines the process within your Woocommerce Dashboard. Navigate the Order Details page, click on "Refund" and specify the refund amount, and optionally the reason.

<figure><img src="https://payswitcher.com/img/site/wordpress_refund.png" alt=""><figcaption></figcaption></figure>

Note: Ensure you click on "Refund via PaySwitcher" and not the "Refund manually". PaySwitcher will handle the refund and update the payment status accordingly, ensuring a seamless refund experience for both you and your customers.

#### 2.3 Payment Sync:

With the PaySwitcher plugin integrated into your Woocommerce Dashboard, you have the flexibility to manually sync payment status whenever necessary. This feature allows you to ensure accurate payment status representation and maintain consistent order management. Navigate to the Order Details page and click on the "Order Actions" dropdown. Select the "Sync Payment with PaySwitcher" option, and click on "Update".

<figure><img src="https://payswitcher.com/img/site/wordpress_sync.png" alt=""><figcaption></figcaption></figure>

The payment status will be accurately reflected, whether the payment is processing, succeeded, or failed.

#### 2.4 Order Updates via Webhooks:

PaySwitcher facilitates seamless order updates through webhooks, allowing you to automate various order management processes. By setting up webhooks within your PaySwitcher Plugin Settings and configuring the necessary endpoints in your PaySwitcher Dashboard, you can receive real-time notifications about order status changes, payment confirmations, and more.

<figure><img src="https://payswitcher.com/img/site/wordpress_webhook.png" alt=""><figcaption></figcaption></figure>

This enables you to trigger specific actions or update order information in your Woocommerce system, ensuring smooth order processing and fulfillment.
