---
description: >-
  Fish Wishlist supports Klaviyo integration via Shopify Flow. This allows you
  to trigger Klaviyo events when customers add or remove products from their
  wishlist.
icon: envelope
---

# Klaviyo

***

### How it works

When a customer adds or removes a product from their wishlist, Fish Wishlist creates a **Shopify Flow trigger**. You can then use Shopify Flow to send event data to Klaviyo as events.

We’ve created **ready-to-use templates** to help you get started quickly.

***

### Prerequisites

To use this integration, you’ll need:

* Fish Wishlist installed and active on your Shopify store
* Klaviyo installed and integrated with Shopify
* Shopify Flow installed (free for Shopify and Shopify Plus plans)
* Your **Klaviyo Private API Key** (for sending event data)

***

### Available Templates

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

You can load our prebuilt Shopify Flow templates here:\
👉 [Use Templates](https://admin.shopify.com/apps/flow/editor/templates?apps=157109354497)

#### 1. Trigger marketing campaign when customer adds product to wishlist

Sends a custom event to Klaviyo when a product is added to a wishlist.\
**Useful for flows like:** “Send a reminder if item hasn’t been purchased in X days.”

#### 2. Cancel marketing campaign when customer removes product from wishlist

Sends a custom event to Klaviyo when a product is removed from a wishlist.\
**Useful for flows like:** “Stop reminding users about items they’re no longer interested in.”

***

### Customizing the Flow

Each template delivers events to Klaviyo. You can customize the payload based on your needs.

The only field you have to populate is your Klaviyo Public API Key. To fetch this, Navigate to "Account > Settings > API Keys" inside Klaviyo app.

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

Once you have added your API key, you can publish the Flow and wishlist data will start flowing through to Klaviyo.

***

### Notes

* This integration is managed entirely via **Shopify Flow**
* Fish Wishlist triggers do not require any additional setup
* You can customize your own flows beyond the provided templates

***

### Support

Need help or want a custom flow? [Contact us](https://app.gitbook.com/u/ORl9VeaRJSOs4nsMpInXf0lzgvu2) — we're happy to help you set it up.
