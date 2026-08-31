---
description: >-
  Every Shopify Flow trigger published by Fish Wishlist, when it fires, and the
  fields it makes available to your workflow.
icon: bolt
---

# Flow Triggers Reference

Fish Wishlist publishes nine triggers to Shopify Flow. Search for `wishlist` in the Flow trigger picker to find them all.

Every trigger includes an **Event ID** field — a unique identifier for that individual event. It's mainly useful for de-duplication if you're forwarding events to an external system.

***

## Product triggers

### Product Added to Wishlist

Fires the moment a customer saves a product variant to any of their wishlists. This is the most commonly used trigger.

| Field              | Type     | Notes                                                                                    |
| ------------------ | -------- | ---------------------------------------------------------------------------------------- |
| **Customer**       | Customer | Full Shopify customer reference                                                          |
| **Product**        | Product  | Full Shopify product reference                                                           |
| **Variant ID**     | Text     | The specific variant the customer saved                                                  |
| **Wishlist ID**    | Text     | Which list it was saved to — see [Wishlist IDs](flow-triggers-reference.md#wishlist-ids) |
| **Wishlist title** | Text     | The customer-facing name of the list                                                     |
| **Event ID**       | Text     | Unique ID for this event                                                                 |

**Good for:** tagging high-intent customers, "still thinking about it?" reminder emails, pushing an event to your ESP.

### Product Removed from Wishlist

Fires when a customer removes a saved product from a wishlist. Carries the same fields as **Product Added to Wishlist**.

**Good for:** cancelling a reminder sequence, removing a tag or segment membership so you stop marketing an item the customer no longer wants.

***

## Alert triggers

These two triggers power the alerts merchants ask for most. Both need a little more care than the others — read [Set Up Wishlist Alerts](set-up-wishlist-alerts.md) for the full walkthrough.

### Wishlist Product Back in Stock

Fires when a product variant sitting on a customer's wishlist comes back into stock. One event is sent per customer who has that variant saved.

| Field          | Type     | Notes                            |
| -------------- | -------- | -------------------------------- |
| **Customer**   | Customer | The customer waiting on the item |
| **Product**    | Product  | The product that restocked       |
| **Variant ID** | Text     | The variant that restocked       |
| **Event ID**   | Text     | Unique ID for this event         |

{% hint style="warning" %}
Fish Wishlist only listens for restocks while you have a **live workflow using this trigger**. Turning the workflow off stops the tracking, and turning it back on resumes it. Restocks that happen while no workflow is on are not backfilled.
{% endhint %}

### Wishlist Product Price Drop

Fires when the price of a variant on a customer's wishlist falls below the price we last recorded for it. One event is sent per customer who has that variant saved.

| Field              | Type     | Notes                                             |
| ------------------ | -------- | ------------------------------------------------- |
| **Customer**       | Customer | The customer who saved the item                   |
| **Product**        | Product  | The product whose price dropped                   |
| **Variant ID**     | Text     | The variant whose price dropped                   |
| **Wishlist ID**    | Text     | Which list the item is on                         |
| **Wishlist title** | Text     | The customer-facing name of the list              |
| **Old price**      | Decimal  | The price we previously recorded                  |
| **New price**      | Decimal  | The current, lower price                          |
| **Currency**       | Text     | Reserved; read the price from `product` if needed |
| **Event ID**       | Text     | Unique ID for this event                          |

{% hint style="info" %}
Price drops are detected by a scheduled check that runs **once an hour**, so these events arrive within the hour rather than instantly. Your baseline prices are recorded the first time you turn on a workflow using this trigger — see [Set Up Wishlist Alerts](set-up-wishlist-alerts.md).
{% endhint %}

***

## Wishlist triggers

### Wishlist Created

Fires when a customer creates a new wishlist. On stores using multiple wishlists per customer this fires each time they add a list; on single-wishlist stores it fires once, the first time they save anything.

| Field              | Type     |
| ------------------ | -------- |
| **Customer**       | Customer |
| **Wishlist ID**    | Text     |
| **Wishlist title** | Text     |
| **Event ID**       | Text     |

**Good for:** a welcome email explaining how the wishlist works, or tagging first-time wishlist users.

### Wishlist Removed

Fires when a customer deletes one of their wishlists. Carries the same fields as **Wishlist Created**.

### Shared Wishlist Created

Fires when a customer shares a wishlist using the [share feature](../wishlist-sharing.md).

| Field                     | Type     | Notes                                         |
| ------------------------- | -------- | --------------------------------------------- |
| **Customer**              | Customer | The customer doing the sharing                |
| **Wishlist ID**           | Text     | Which list was shared                         |
| **Wishlist title**        | Text     | The customer-facing name of the list          |
| **Shared Wishlist URL**   | Text     | The public link to the shared list            |
| **Shared Wishlist items** | Text     | The contents of the list, as JSON — see below |
| **Event ID**              | Text     | Unique ID for this event                      |

Flow trigger fields can't hold lists, so the items travel as a JSON string: an array of objects with `product_id`, `variant_id`, `product_title` and `variant_title`. Pass it straight through to an external service in a **Send HTTP request** action, where it can be parsed.

**Good for:** emailing the customer their share link, or sending the full list contents to an email platform for a gift-guide campaign.

***

## Collection triggers

### Collection Added to Wishlist

Fires when a customer saves a whole collection to their wishlist.

| Field                 | Type     |
| --------------------- | -------- |
| **Customer**          | Customer |
| **Collection ID**     | Text     |
| **Collection title**  | Text     |
| **Collection handle** | Text     |
| **Event ID**          | Text     |

{% hint style="info" %}
Shopify Flow only supports full references for customers, orders and products, so collections arrive as plain text fields rather than a collection reference.
{% endhint %}

### Collection Removed from Wishlist

Fires when a customer removes a saved collection. Carries the same fields as **Collection Added to Wishlist**.

**Good for:** category-level interest signals — segmenting customers by the collections they follow.

***

## Wishlist IDs

The **Wishlist ID** field holds an internal identifier in the form `WL1`, `WL2`, and so on. `WL1` is the customer's default wishlist. Two IDs are managed by the app rather than the customer:

| ID     | Wishlist             |
| ------ | -------------------- |
| `WL11` | Abandoned Cart       |
| `WL12` | Previously Purchased |

If a workflow should only respond to lists the customer built themselves, add a Flow condition checking that **Wishlist ID** is not `WL11` or `WL12`.
