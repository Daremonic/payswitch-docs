---
description: >-
  PaySwitcher is designed to facilitate the integration and management of
  payment-related functionalities in a decoupled or headless architecture with
  flexibility to customize your checkout UI.
---

# Headless SDK

{% hint style="info" %}
This section guides you through the integration of PaySwitcher Headless for both web and mobile clients
{% endhint %}

### Customize the payment experience using Headless functions

#### 1. Initialize the PaySwitcher SDK

Initialize  PaySwitcher Headless SDK onto your app with your publishable key. To get a Publishable Key please find it [here](https://app.payswitcher.com/developers).

{% tabs %}
{% tab title="HTML + JavaScript" %}
<pre class="language-javascript"><code class="lang-javascript"><strong>// Source Hyperloader on your HTML file using the &#x3C;script /> tag
</strong>hyper = Hyper.init(YOUR_PUBLISHABLE_KEY);
</code></pre>
{% endtab %}

{% tab title="Flutter" %}
```dart
// dependencies: flutter_payswitcher: ^version_number
// run the following command to fetch and install the dependencies flutter pub get
import 'package:flutter_payswitcher/flutter_payswitcher.dart';
_hyper.init(HyperConfig(publishableKey: 'YOUR_PUBLISHABLE_KEY'));
```
{% endtab %}

{% tab title="React Native (Beta)" %}
```javascript
import { HyperProvider } from "@payswitcher/react-native-payswitcher ";

function App() {
  return (
    <HyperProvider publishableKey="YOUR_PUBLISHABLE_KEY">
      // Your app code here
    </HyperProvider>
  );
}
```
{% endtab %}
{% endtabs %}

#### 2. Create a Payment Intent

Make a request to the endpoint on your server to create a new Payment. The `clientSecret` returned by your endpoint is used to initialize the payment session.

{% hint style="danger" %}
**Important**: Make sure to never share your API key with your client application as this could potentially compromise your security
{% endhint %}

#### 3. Initialize your Payment Session

Initialize a Payment Session by passing the clientSecret to the `initPaymentSession`

{% tabs %}
{% tab title="JavaScript" %}
```javascript
paymentSession = hyper.initPaymentSession({
  clientSecret: client_secret,
});
```
{% endtab %}

{% tab title="Flutter" %}
```dart
final params = PaymentMethodParams(clientSecret: 'YOUR_PAYMENT_INTENT_CLIENT_SECRET')
Session _sessionId = await hyper.initPaymentSession(params);
```
{% endtab %}

{% tab title="React Native  (Beta)" %}
```javascript
import { useHyper } from "@payswitcher/react-native-payswitcher";

const { initPaymentSession } = useHyper();
const [paymentSession,setPaymentSession]=React.useState(null);
const initializeHeadless = async () => {

  const { clientSecret } = await fetchPaymentParams();
  const params={clientSecret:clientSecret}
  const paymentSession = await initPaymentSession(params);
  setPaymentSession(_=>paymentSession)
};

useEffect(() => {
  initializeHeadless();
}, []);

```
{% endtab %}
{% endtabs %}

| options (Required)      | Description                                                      |
| ----------------------- | ---------------------------------------------------------------- |
| `clientSecret (string)` | **Required.**  Required to use as the identifier of the payment. |

#### 4. Craft a customized payments experience

Using the `paymentSession` object, the default customer payment method data can be fetched, using which you can craft your own payments experience. The `paymentSession` object also exposes a `confirmWithCustomerDefaultPaymentMethod` function, using which you can confirm and handle the payment session.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
paymentMethodSession = await paymentSession.getCustomerSavedPaymentMethods();

if (paymentMethodSession.error) {
    // handle the case where no default customer payment method is not present
} else {
    // use the customer_default_saved_payment_method_data to fulfill your usecases (render UI)
    const customer_default_saved_payment_method_data =
        paymentMethodSession.getCustomerDefaultSavedPaymentMethodData();
}

//handle press for pay button 
function handlePress() { 
    if (paymentMethodSession.error) {
        // handle the case where no default customer payment method is not present
    } else {
        // use the confirmWithCustomerDefaultPaymentMethod function to confirm and handle the payment session response
        const { error, status } = await
        paymentMethodSession.
            confirmWithCustomerDefaultPaymentMethod({
                confirmParams: {
                    // Make sure to change this to your payment completion page
                    return_url: "https://example.com/complete"
                },
                // if you wish to redirect always, otherwise it is defaulted to "if_required"
                redirect: "always",
            });

        // use error, status to complete the payment journey
        if (error) {
            if (error.message) {
                // handle error messages
                setMessage(error.message);
            } else {
                setMessage("An unexpected error occurred.");
            }
        }
        if (status) {
            // handle payment status
            handlePaymentStatus(status);
        }
    }
}
```
{% endtab %}

{% tab title="Flutter" %}
```dart
SavedSession? _savedSessionId = await _hyper.getCustomerSavedPaymentMethods(_sessionId!);

// use the customer_default_saved_payment_method_data to fulfill your usecases
final customer_default_saved_payment_method_data = await _hyper.getCustomerDefaultSavedPaymentMethodData(_savedSessionId!);
if (customer_default_saved_payment_method_data != null) {
    final paymentMethod = customer_default_saved_payment_method_data.left;
    if (paymentMethod != null) {
       final card = paymentMethod.left;
       if (card != null) {
          setState(() {
            _defaultPMText = "${card.nickName}  ${card.cardNumber}  ${card.expiryDate}";
          });
       } else {
          final wallet = paymentMethod.right;
          if (wallet != null) {
            setState(() {
              _defaultPMText = wallet.walletType;
            });
          }
       }
    } else {
      final err = customer_default_saved_payment_method_data.right;
      setState(() {
        _defaultPMText = err?.message ?? "No Default Payment Method present";
      });
    }
  }
}

// use the confirmWithCustomerDefaultPaymentMethod function to confirm and handle the payment session response
Future<void> _confirmPayment() async {
  final confirmWithCustomerDefaultPaymentMethodResponse = 
    await _hyper.confirmWithCustomerDefaultPaymentMethod(_savedSessionId!);
  if (confirmWithCustomerDefaultPaymentMethodResponse != null) {
    final message = confirmWithCustomerDefaultPaymentMethodResponse.message;
    if (message.isLeft) {
      _confirmStatusText = "${confirmWithCustomerDefaultPaymentMethodResponse.status.name}\n${message.left!.name}";
    } else {
      _confirmStatusText = "${confirmWithCustomerDefaultPaymentMethodResponse.status.name}\n${message.right}";
    }
  }
}
```
{% endtab %}

{% tab title="React Native  (Beta)" %}
```javascript
import { useHyper } from "@payswitcher/react-native-payswitcher";

const { getCustomerSavedPaymentMethods,
        getCustomerDefaultSavedPaymentMethodData,
        confirmWithCustomerDefaultPaymentMethod } = useHyper();

const [defaultPaymentMethodData,setDefaultPaymentMethodData]=React.useState(null)

React.useEffect(()=>{
    const getPaymentMethods=async()=>{
    const paymentMethodSession = await getCustomerSavedPaymentMethods(paymentSession);
    const customer_default_saved_payment_method_data = await getCustomerDefaultSavedPaymentMethodData(paymentMethodSession);
    setDefaultPaymentMethodData(_=>customer_default_saved_payment_method_data)
    }
    getPaymentMethods()
},[])

let confirmDefaultPaymentMethod=()=>{
const status = await confirmWithCustomerDefaultPaymentMethod(paymentMethodSession);
// handle status of payment   
 if (status != null) {
    const message = status.message;
    console.log(message)
    }
}

return(
//build the ui using defaultPaymentMethodData
//on click of pay use confirmDefaultPaymentMethod()
)
```
{% endtab %}
{% endtabs %}

&#x20;**Payload for** `confirmWithCustomerDefaultPaymentMethod(payload)`

<table><thead><tr><th width="296">options (Required)</th><th>Description</th></tr></thead><tbody><tr><td><code>confirmParams (object)</code></td><td>Parameters that will be passed on to the Hyper API.</td></tr><tr><td><code>redirect (string)</code></td><td><p><strong>(web only)</strong> <strong>Can be either 'always' or 'if_required'</strong> </p><p>By default, <code>confirmWithCustomerDefaultPaymentMethod()</code> will always redirect to your <code>return_url</code> after a successful confirmation. If you set redirect: "if_required", then this method will only redirect if your user chooses a redirection-based payment method.</p></td></tr></tbody></table>

**ConfirmParams object**

<table><thead><tr><th width="281">confirmParams</th><th>Description</th></tr></thead><tbody><tr><td><code>return_url(string)</code></td><td><strong>(web only)</strong> The url your customer will be directed to after they complete payment.</td></tr></tbody></table>
