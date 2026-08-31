---
description: >-
  Send back-in-stock and price-drop alerts, tag customers and push wishlist
  events to any marketing tool — using Fish Wishlist triggers in Shopify Flow.
icon: diagram-project
---

# Shopify Flow

Every meaningful thing a customer does with their wishlist — saving a product, sharing a list, or waiting on an item that just came back in stock — is published to **Shopify Flow** as a trigger. From there you can build any workflow Flow supports: send an email or SMS, tag the customer, add them to a segment, post to Slack, or call an external API such as Klaviyo, Attentive or Dotdigital.

***

### Before you start

* **Fish Wishlist** installed on your store.
* **Shopify Flow** installed. It's free from the [Shopify App Store](https://apps.shopify.com/flow) on all Shopify plans.

Once both apps are installed, the Fish Wishlist triggers appear automatically in the Flow editor. There is nothing to enable inside Fish Wishlist.

***

### Building your first workflow

1. Open **Shopify Flow** from your Shopify admin.
2. Click **Create workflow**, then **Select a trigger**.
3. Search for `wishlist`. All Fish Wishlist triggers are listed under the **Fish Wishlist** app.
4. Pick a trigger, add your conditions and actions, then click **Turn on workflow**.

{% hint style="warning" %}
A workflow only runs while it is **turned on**. A draft workflow receives nothing, and for the Back in Stock and Price Drop triggers this matters more than usual — see [Set Up Wishlist Alerts](set-up-wishlist-alerts.md).
{% endhint %}

***

### In this section

* [**Flow Triggers Reference**](flow-triggers-reference.md) — every trigger we publish, when it fires and the data it carries.
* [**Set Up Wishlist Alerts**](set-up-wishlist-alerts.md) — step-by-step back-in-stock and price-drop alerts.
* [**Flow Templates**](flow-templates.md) — our ready-made workflows you can install in one click.

***

### Using wishlist data in your actions

Every trigger exposes its fields as Flow variables. The two you'll reach for most often are:

* `customer` — a full Shopify customer reference, so you can use `customer.email`, `customer.firstName`, `customer.tags` and so on, and send email directly to the customer.
* `product` — a full Shopify product reference (on the product-level triggers), giving you `product.title`, `product.onlineStoreUrl`, `product.featuredImage` and more.

The remaining fields arrive as plain text or numbers. See the [Flow Triggers Reference](flow-triggers-reference.md) for the exact list per trigger.

***

### Need a hand?

Building something more involved, or want us to set a workflow up for you? [Contact us](../faq/contact-us.md) — we're happy to help.
