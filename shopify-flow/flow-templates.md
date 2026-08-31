---
description: >-
  Pre-built Shopify Flow workflows from Fish Wishlist that you can install in
  one click and customise from there.
icon: wand-magic-sparkles
---

# Flow Templates

Rather than building a workflow from scratch, you can start from one of ours. Templates arrive pre-wired to the right Fish Wishlist trigger with the actions already in place — you fill in your credentials and turn it on.

👉 [**Browse Fish Wishlist templates in Shopify Flow**](https://admin.shopify.com/apps/flow/editor/templates?apps=157109354497)

You can also find them from inside Flow: click **Create workflow**, then **Start with a template**, and search for `wishlist`.

***

## Available templates

### Trigger marketing campaign when customer adds product to wishlist

Sends a custom event to **Klaviyo** whenever a customer saves a product, so you can start a Klaviyo flow from it.

* **Trigger:** Product Added to Wishlist
* **Setup required:** your Klaviyo API key in the **Track an Event** block
* **Useful for:** "still interested?" reminders a few days after saving, wishlist-based segments, abandoned-browse style campaigns

### Cancel marketing campaign when customer removes product from wishlist

The counterpart to the template above — sends a Klaviyo event when a customer removes a product, so you can stop marketing something they've lost interest in.

* **Trigger:** Product Removed from Wishlist
* **Setup required:** your Klaviyo API key in the **Track an Event** block
* **Useful for:** exiting customers from a reminder sequence, keeping segments clean

{% hint style="info" %}
Both templates need your Klaviyo API key before they'll work. You'll find it in Klaviyo under **Account → Settings → API Keys**. The full walkthrough is on the Klaviyo integration page.
{% endhint %}

***

## Installing a template

1. Open the [template list](https://admin.shopify.com/apps/flow/editor/templates?apps=157109354497) or find it in Flow under **Create workflow → Start with a template**.
2. Click the template, then **Select template**. Flow opens an editable copy — the original is never modified.
3. Open each action step and fill in anything marked as required (for the Klaviyo templates, that's your API key).
4. Adjust the payload, add conditions, or swap in a different action if you want.
5. Click **Turn on workflow**.

A template is only a starting point. Once installed it's an ordinary Flow workflow: add steps, change the trigger conditions, or send the data somewhere else entirely.

***

## Building your own

Every Fish Wishlist trigger is available for custom workflows, not just the ones covered by templates. The [Flow Triggers Reference](flow-triggers-reference.md) lists all nine with their fields, and [Set Up Wishlist Alerts](set-up-wishlist-alerts.md) walks through building back-in-stock and price-drop workflows from scratch.

Want a template for a platform we don't cover yet? Let us know — we build these based on what merchants ask for.
