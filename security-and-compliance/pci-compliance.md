---
description: A brief summary of PCI compliance for PaySwitcher Cloud users
---

# 💳 PCI Compliance

PaySwitcher Cloud offers **out-of-the-box PCI compliance**, so that you do not have to worry about securing and storing customers's cards.

## PCI DSS Level 1 compliance <a href="#docs-internal-guid-959e0903-7fff-fc13-1542-001b2640a715" id="docs-internal-guid-959e0903-7fff-fc13-1542-001b2640a715"></a>

PaySwitcher is Level 1 PCI DSS 3.2.1 certified which is the strictest level of compliance to handle card data securely.

The infrastructure and application are annually audited with a PCI approved scanning vendor to keep the PCI compliance up to date.

## Enabling raw card acceptance with payment processors <a href="#docs-internal-guid-959e0903-7fff-fc13-1542-001b2640a715" id="docs-internal-guid-959e0903-7fff-fc13-1542-001b2640a715"></a>

While you are using PaySwitcher, your customers' cards will be securely tokenized and stored on PaySwitcher Cloud vault.

However this will require the payment processors to enable raw card acceptance at their end (which most payment processor do not offer as default setting). You will have to send PaySwitcher PCI AOC to your payment processor's support team and request to enable the setting against your merchant account.

{% hint style="info" %}
Please drop a note to `biz@payswitcher.com` to get access to the PaySwitcher PCI AOC (applicable only for PaySwitcher Cloud users
{% endhint %}

If you are planning to use PaySwitcher Open Source, please [refer here](broken-reference/) for more notes about ensuring PCI compliance when you self deploy PaySwitcher
