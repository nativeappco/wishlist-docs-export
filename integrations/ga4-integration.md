---
description: >-
  With GA4 integration, Fish Wishlist helps Shopify merchants track “Add to
  Wishlist” events for Google Analytics 4. GA4 integration is enabled by default
  and you can easily toggle it on and off.
icon: google
---

# GA4 Integration

This data provides valuable insights into customer preferences and lets you see which products are popular with your audience.

### Key Benefits

1. **Track Wishlist Events in GA4**:\
   Automatically captures “Add to Wishlist” actions and sends them to GA4 for reporting. Track events such as:
   * **Product ID**: Identifies specific products added to wishlists.
   * **Product Name**: Records the product name, making it easy to track which items customers are interested in.
2. **Hassle-Free Setup**:\
   GA4 tracking is enabled by default, so you can start monitoring wishlist activity in GA4 without any additional setup. For custom tracking needs, you can disable this feature anytime.

### How It Works

1.  **Automatic Tracking Setup**:\
    Fish Wishlist has built-in GA4 event tracking for “Add to Wishlist” events, which is turned on by default. You can verify or modify this in the app’s admin settings if necessary.

    <figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>
2. **Data Captured**:\
   Each time a customer adds a product to their wishlist, Fish Wishlist sends a GA4 “add\_to\_wishlist” event with product details. This makes it easy to monitor which products are popular across your site.
3. **GA4 Reporting**:\
   Access your “Add to Wishlist” events in GA4 to analyze customer interests. You can also use these insights for retargeting or promotional campaigns.

### Example Data Sent

* **Event Name**: `add_to_wishlist`
* **Product ID**: Tracked as `item_id`
* **Product Name**: Captured as `item_name` for easy identification.

### Troubleshooting

* **Existing GA4 Setup**: If your store already uses a custom GA4 setup, you can disable Fish Wishlist’s GA4 integration in the settings.
* **Missing Product Data**: If product information doesn’t show as expected in GA4, double-check that the app's GA4 integration is enabled and that your GA4 setup is configured to accept wishlist events.



