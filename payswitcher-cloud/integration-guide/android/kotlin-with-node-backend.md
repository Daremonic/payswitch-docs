---
description: Integrate hyper SDK to your Kotlin App using payswitcher-node
---

# Kotlin with Node Backend

{% hint style="info" %}
In this section, you will get detailed instructions for integrating the PaySwitcher native Android SDK for your Android app
{% endhint %}

{% hint style="info" %}
Use this guide to integrate hyper SDK to your Android app. You can use this as a reference with your PaySwitcher credentials to test the setup. You can also checkout the [App on Google Play Store](https://play.google.com/store/apps/details?id=io.payswitcher.hyperecom) to test the payment flow.
{% endhint %}

## Requirements

* Android 5.0 (API level 21) and above
* [Android Gradle Plugin](https://developer.android.com/studio/releases/gradle-plugin) 7.3.1
* [Gradle](https://gradle.org/releases/) 7.5.1+
* [AndroidX](https://developer.android.com/jetpack/androidx/)

## 1. Setup the server

### 1.1 Install the `payswitcher-node` library

Install the package and import it in your code

```js
$ npm install @payswitcher/payswitcher-node
```

### 1.2 Create a payment

Before creating a payment, import the `payswitcher-node` dependencies and initialize it with your API key.

```js
const hyper = require("@payswitcher/hyperwitch-node")(‘YOUR_API_KEY’);
```

Add an endpoint on your server that creates a Payment. Creating a Payment helps to establish the intent of the customer to start a payment. It also helps to track the customer’s payment lifecycle, keeping track of failed payment attempts and ensuring the customer is only charged once. Return the `client_secret` obtained in the response to securely complete the payment on the client.

```js
// Create a Payment with the order amount and currency
app.post("/create-payment", async (req, res) => {
  try {
    const paymentIntent = await hyper.paymentIntents.create({
      currency: "USD",
      amount: 100,
    });
    // Send publishable key and PaymentIntent details to client
    res.send({
      clientSecret: paymentIntent.client_secret,
    });
  } catch (err) {
    return res.status(400).send({
      error: {
        message: err.message,
      },
    });
  }
});
```

## 2. Build checkout page on your app

### 2.1 Configure your repository with PaySwitcher dependency

Add the following maven repository to the settings.gradle file

```js
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        google()
        mavenCentral()
           maven {
            url "https://maven.payswitcher.com/release/production/android/maven/1.2.7"
        }
    }
}
```

### 2.2 Add the PaySwitcher dependency

Add payswitcher-android to the dependencies block of your build.gradle file to install the SDK

```groovy
dependencies {

    // PaySwitcher Android SDK
    implementation 'io.payswitcher:payswitcher-android:+'
}
```

### 2.3 Implement the HyperInterface

Implement the HyperInterface to your CheckoutActivity

```java
class CheckoutActivity : AppCompatActivity(), HyperInterface {

    // ...
}

```

### 2.4 Setup the SDK and fetch a Payment

Setup the SDK with your publishable key

```java
PaymentConfiguration.init(applicationContext, "YOUR_PUBLISHABLE_KEY");
```

{% hint style="info" %}
Note: For the Setup, initialise PaymentConfiguration as:

<pre class="language-bash"><code class="lang-bash"><strong>PaymentConfiguration.initWithBackend(applicationContext, "YOUR_PUBLISHABLE_KEY", "YOUR_SERVER_URL");
</strong></code></pre>
{% endhint %}

Fetch a payment by requesting your server for a payment as soon as your view is loaded. Store a reference to the `client_secret` returned by the server; the Payment Sheet will use this secret to complete the payment later.

## 3. Complete the payment on your app

Create a PaymentSheet instance using the `client_secret` retrieved from the previous step. Present the payment page from your view controller and use the PaymentSheet.Configuration struct for customising your payment page.

```java
val configuration = PaymentSheet.Configuration("Your_app, Inc.")

// Present Payment Page
paymentSheet.presentWithPaymentIntent(paymentIntentClientSecret, configuration)
```

Handle the payment result in the completion block and display appropriate messages to your customer based on whether the payment fails with an error or succeeds.

```java
private fun onPaymentSheetResult(paymentResult: PaymentSheetResult) {
        when (paymentResult) {
            is PaymentSheetResult.Completed -> {
                showToast("Payment complete!")
            }
            is PaymentSheetResult.Canceled -> {
                Log.i(TAG, "Payment canceled!")
            }
            is PaymentSheetResult.Failed -> {
                showAlert("Payment failed", paymentResult.error.localizedMessage)
            }
        }
    }
```

Congratulations! Now that you have integrated the Android SDK, you can customise the payment sheet to blend with the rest of your app.

## Next step:

{% content-ref url="../../payment-methods-setup/" %}
[payment-methods-setup](../../payment-methods-setup/)
{% endcontent-ref %}
