---
description: Start accepting one time payments with PaySwitcher in 4 easy steps
---

# ⚡ Quickstart

{% hint style="info" %}
This section gives you the steps to get started with PaySwitcher, configure your payment processor, integrate with your application and accept your first payment in minutes
{% endhint %}

## Getting Started

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><strong>Quickstart guide</strong></td><td>Integrate PaySwitcher from scratch and accept your first payment in minutes</td><td></td><td><a href="./#get-your-payswitcher-api-key">#get-your-payswitcher-api-key</a></td><td><a href="../../.gitbook/assets/quickstart.jpg">quickstart.jpg</a></td></tr><tr><td><strong>Migrate from Stripe</strong></td><td>Already a Stripe user? Learn how you can quickly migrate to PaySwitcher</td><td></td><td><a href="migrate-from-stripe/">migrate-from-stripe</a></td><td><a href="../../.gitbook/assets/StripeMigration.jpg">StripeMigration.jpg</a></td></tr><tr><td><strong>Payment recipes</strong></td><td>Explore quick payment recipes consisting of combinations of use case specific payment processors</td><td></td><td><a href="payment-recipes/">payment-recipes</a></td><td><a href="../../.gitbook/assets/recipe.jpg">recipe.jpg</a></td></tr></tbody></table>

## Get your PaySwitcher API key

If you have not created a sandbox account, please create one

[Sign Up for PaySwitcher](https://app.payswitcher.com/register)

If you have already created a sandbox account, your api key could be fetched from [settings section](https://app.payswitcher.com/developers).

## Configure your payment processor

Configure the payment processor of your choice using [Connectors](https://app.payswitcher.com/connectors) tab on our control center. You will need to have the API credentials of the payment processor readily available.

If you do not have access to the API credentials of your payment processor, do not worry. PaySwitcher has a demo payment processor automatically configured to your sandbox account. It will assist you to simulate various payment flows and assist you in completing the integration.

## Integrate PaySwitcher

The payment flow begins once your user has added products to a shopping cart and now wishes to make a payment.

**Step 1:** Your server will create a payment with PaySwitcher server, to get a client\_secret.

**Step 2:** Your website loads and initiates the [PaySwitcher SDK](../integration-guide/) to render a payment widget to the customer. Depending on the customer's currency and country, the list of payment methods are displayed to the customer.

**Step 3:** The customer chooses a payment method, enters additional information (say card details) and hits the pay button.

**Step 4:** PaySwitcher SDK securely transmits the payment information to PaySwitcher Server. The PaySwitcher server processes the payment with the most suitable payment processor, as per the your smart routing algorithm.

**Step 5:** Upon successful payment, the customer is automatically redirected to your payment status confirmation page.

<figure><img src="../../.gitbook/assets/image (97).png" alt=""><figcaption></figcaption></figure>

## Configure and manage payment methods on the PaySwitcher Control Center

The control center provides complete control on your payment operations.

* **Enable and manage payment processors:** Easily onboard multiple payment processors and manage payment methods with a few clicks.
* **Track payment and refund information:** The unified control center allows you to query upon a particular payment or refund. You may also initiate refunds from the control center.
* **Smart payment routing:** You will have the complete capability to dynamically set the payment routing logic based on 20+ variables. Use this to optimize your payment processing goals.

<details>

<summary>FAQs</summary>

**What is a connector?**

PaySwitcher refers to payment processors, fraud / risk engines and other payment integrations as connectors. PaySwitcher currently supports 50+ global payment processors that you can use to process payments on your application

**How can I decide the best payment methods for my business?**

PaySwitcher supports 100+ payment methods across various payment processors. There is no one size fits all payment methods but you can learn more about how you can decide the best payment methods for you business [here](../payment-methods-setup/).

**What will the completed integration look like?**

PaySwitcher offers various customization options but you can try out our demo store [here](https://demo-payswitcher.netlify.app/checkout) to test the checkout experience

**Are there any sample integrations for reference?**

Here are a few demo integrations for various tech stacks:

* [PaySwitcher React-Node](https://github.com/payswitcher/payswitcher-react-node)
* [PaySwitcher HTML-Node](https://github.com/payswitcher/payswitcher-html-node)
* [PaySwitcher React-Java](https://github.com/payswitcher/payswitcher-react-java)
* [PaySwitcher Next-Node](https://github.com/payswitcher/payswitcher-next-node)

</details>
