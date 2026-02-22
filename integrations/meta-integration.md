---
description: >-
  The Meta Integration in the Fish Wishlist app makes it easy to track and use
  wishlist actions on Facebook and Instagram for effective marketing.
icon: facebook-f
---

# Meta Integration

With just a few clicks, you can set up tracking for “Add to Wishlist” events, which helps you reach customers on social media based on what they love.

### Key Benefits

1. **Track Wishlist Events**:\
   Automatically sends “Add to Wishlist” data to Meta, which you can use to create ads for Facebook and Instagram. This includes:
   * **Product IDs**: Tracks which product was added to the wishlist.
   * **Product Names**: Captures the item name for better reporting and targeting.
2. **Simple Setup in Admin Settings**:\
   Meta tracking is pre-enabled in your app's admin settings, so it's ready to go right away. For stores with custom tracking, you can easily turn off this feature if needed.

### How It Works

1. **Easy Configuration**:\
   By default, Meta Integration is switched on. You can go to Admin -> Settings to verify it or disable it if your store has another tracking setup.\
   ![](<../.gitbook/assets/image (3).png>)
2. **Tracking in Action**:\
   When a customer adds an item to their wishlist, Fish Wishlist sends the “Add to Wishlist” event directly to Meta with all the details.
3. **Verify with Meta Pixel Helper**:\
   Use the Meta Pixel Helper Chrome extension to confirm tracking is active. If the pixel isn’t detected, check your store’s theme and ensure custom scripts are enabled.

### Example Data

* **Product ID**: Sent with the event as `content_ids`.
* **Product Name**: Captured as `content_name` for easy identification.



### Troubleshooting

* **Already Have a Pixel?** No problem. Just turn off the Meta Integration in settings if your store has its own tracking solution.
* **Extensions Not Detecting**: If there’s an issue with detection, double-check that tracking is enabled in your store theme settings.
