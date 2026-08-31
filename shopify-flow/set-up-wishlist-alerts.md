---
description: >-
  Send your customers a back-in-stock or price-drop email the moment a product
  on their wishlist becomes available or goes on sale — built entirely in
  Shopify Flow.
icon: bell
---

# Set Up Wishlist Alerts

Back-in-stock and price-drop alerts are the highest-converting thing you can do with a wishlist: the customer has already told you exactly what they want. Both are built in Shopify Flow using Fish Wishlist triggers, and neither needs any code.

***

## Back in stock alerts

Notify every customer with a sold-out item on their wishlist as soon as it's available again.

### 1. Create the workflow

1. Open **Shopify Flow** and click **Create workflow**.
2. Click **Select a trigger** and search for `wishlist`.
3. Choose **Wishlist Product Back in Stock**.

### 2. Add the email action

1. Click the **+** below the trigger and choose **Send internal email**, or your email platform's action (Klaviyo, Attentive, Omnisend and others all provide Flow actions).
2. To email the customer directly, set the recipient to the `customer.email` variable.
3. Write your subject and body. Useful variables:
   * `{{customer.firstName}}`
   * `{{product.title}}`
   * `{{product.onlineStoreUrl}}` — links straight to the product page
   * `{{product.featuredImage.url}}`

### 3. Turn it on

Click **Turn on workflow**. This step is not optional housekeeping — it's what starts the tracking.

{% hint style="warning" %}
**Turning the workflow on is what enables restock tracking.** Fish Wishlist begins watching your inventory the moment a workflow using this trigger goes live, and stops the moment the last one is turned off. Restocks that happen while no workflow is on are not detected and won't be sent retroactively.
{% endhint %}

### Optional refinements

* **Only alert on real wishlists.** Add a condition that **Wishlist ID** is not `WL11` (Abandoned Cart) or `WL12` (Previously Purchased) if you'd rather not email about app-managed lists.
* **Filter by product.** Add a condition on `product.tags` or `product.productType` to limit alerts to certain ranges.
* **Cap the volume.** Add a condition on `customer.tags` to exclude customers you don't want to email.

***

## Price drop alerts

Tell customers when something they've saved goes on sale.

### 1. Create the workflow

1. In **Shopify Flow**, click **Create workflow** and select a trigger.
2. Search for `wishlist` and choose **Wishlist Product Price Drop**.

### 2. Add a discount threshold (recommended)

A one-cent price change is not worth an email. Add a **Condition** step so only meaningful drops go out:

* Add a condition comparing **New price** to **Old price** — for example, only continue when **New price** is less than `0.9` × **Old price** (a 10% drop or better).

### 3. Add the email action

Same as above. On top of the customer and product variables, the price drop trigger gives you:

* `{{oldPrice}}` — what it used to cost
* `{{newPrice}}` — what it costs now
* `{{wishlistTitle}}` — the list the item is saved on

A subject line like `{{product.title}} just dropped to {{newPrice}}` does the job nicely.

### 4. Turn it on

{% hint style="info" %}
**How price drops are detected.** When you first turn on a workflow using this trigger, Fish Wishlist records the current price of every wishlisted variant as a baseline. From then on a scheduled job compares prices **once an hour** and fires the trigger for any variant that is now cheaper and in stock.

Two consequences worth knowing:

* Alerts arrive **within the hour**, not instantly.
* Price changes made **before** you first turned the workflow on are not detected — the baseline starts at that moment.
{% endhint %}

***

## Testing your alerts

Flow triggers fire from real customer and inventory activity, so the cleanest way to test is end to end:

1. Add a product to a wishlist as a test customer on your storefront.
2. **For back in stock:** set that variant's inventory to `0` in your Shopify admin, wait for it to register, then set it back above `0`.
3. **For price drops:** lower the variant's price, then wait for the next hourly check.
4. Open the workflow in Shopify Flow and check the **Activity** tab — Flow logs every run, including runs that stopped at a condition, so you can see exactly where a workflow halted.

{% hint style="info" %}
Nothing in the Activity log? The two most common causes are a workflow that was never turned on, and a condition that filtered the event out. Check the log first — Flow shows halted runs too.
{% endhint %}

***

## Sending alerts through your email platform

The **Send internal email** action is built into Flow and fine for getting started, but it's plain and hard to brand. For customer-facing alerts, most merchants send the event to their marketing platform instead and design the email there.

If you use Klaviyo, we publish ready-made templates that do exactly this — see [Flow Templates](flow-templates.md) and the [Klaviyo integration guide](../integrations/klaviyo.md).

For any other platform, use Flow's **Send HTTP request** action to post the trigger data to their API.

***

Stuck, or want us to build a workflow for you? [Contact us](../faq/contact-us.md).
