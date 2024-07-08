---
description: Migrate from Stripe on your web app
---

# Web

{% hint style="info" %}
Migrate from Stripe on your web app in less than 15 mins!
{% endhint %}

## Migrate from Stripe

If you are already integrated to Stripe as your payment processor, we have made migrating to PaySwitcher much simpler for you. And once you migrate, get immediate access to 40+ payment processors and features such as Smart Router, Unified analytics and many more.

{% hint style="info" %}
Stripe’s `paymentRequestButton` is available under PaySwitcher’s UnifiedCheckout, therefore importing UnifiedCheckout would be sufficient.
{% endhint %}

The code from your Stripe integration to be removed and replaced is explained below in a step by step manner for both React and HTML frontend. You can find the details for both below.

<details>

<summary>Web - Node Backend and React Frontend</summary>

**Step 1:** Install PaySwitcher's SDK and server side dependencies from npm

```js
  $ npm install @payswitcher/react-hyper-js
  $ npm install @payswitcher/hyper-js
  $ npm install @payswitcher/payswitcher-node
```

**Step 2:** Change the API key on the server side and modify the paymentIntent endpoint from your server side. You can get the API key from [Developers](https://app.payswitcher.com/developers) page on the dashboard.

```js
// from
const stripe = require("stripe")("your_stripe_api_key");
// to
const hyper = require("@payswitcher/payswitcher-node")(
  "your_payswitcher_api_key"
);
```

```js
// from
const paymentIntent = await stripe.paymentIntents.create({
// to
const paymentIntent = await hyper.paymentIntents.create({
```

**Step 3:** Call loadHyper() with you PaySwitcher publishable key to configure the SDK library, from your website

```js
// from
import { loadStripe } from "@stripe/stripe-js";
import { Elements } from "@stripe/react-stripe-js";
// to
import { loadStripe } from "@payswitcher/hyper-js";
import { hyperElements } from "@payswitcher/react-hyper-js";
```

```js
// from
const stripePromise = loadStripe("your_stripe_publishable_key");
// to
const hyperPromise = loadHyper("your_payswitcher_publishable_key");
```

**Step 4:** Configure your checkout form to import from PaySwitcher

```js
//from
import {
  PaymentElement,
  useStripe,
  useElements,
} from "@stripe/react-stripe-js";
//to
import {
  UnifiedCheckout,
  useStripe,
  useElements,
} from "@payswitcher/react-hyper-js";
```

**Step 5:** Run your application to make a test payment. And verify the status of the transaction on PaySwitcher Dashboard and Stripe Dashboard. Congratulations ! You have successfully integrated PaySwitcher to your payments stack and you now have access to a suite of 40+ payment processors and acquirers.

</details>

<details>

<summary>Web - Node Backend and HTML Frontend</summary>

**Step 1:** Install PaySwitcher's node server dependency from npm

```js
  $ npm install @payswitcher/payswitcher-node
```

**Step 2:** Change the API key on the server side and modify the paymentIntent endpoint from your server side

```js
// from
const stripe = require("stripe")("your_stripe_api_key");
// to
const hyper = require("@payswitcher/payswitcher-node")(
  "your_payswitcher_api_key"
);
```

```js
// from
const paymentIntent = await stripe.paymentIntents.create({
// to
const paymentIntent = await hyper.paymentIntents.create({
```

**Step 3:** Load the PaySwitcher directly from beta.payswitcher.com to remain PCI compliant while collecting the customer's payment details

```js
// from
<script src="https://js.stripe.com/v3/"></script>
// to
<script src="https://beta.payswitcher.com/v1/HyperLoader.js"></script>
```

**Step 4:** Initiate the SDK with your PaySwitcher publishable key from your website

```js
// from
const stripe = Stripe("your_stripe_publishable_key");
// to
const hyper = Hyper("your_payswitcher_publishable_key");
```

**Step 5:** Run your application to make a test payment. And verify the status of the transaction on PaySwitcher Dashboard and Stripe Dashboard. Congratulations ! You have successfully integrated PaySwitcher to your payments stack and you now have access to a suite of 40+ payment processors and acquirers.

</details>

Want an easy migration from Stripe for Apps? We got you covered. Follow the docs for Android, iOS and React Native apps.

