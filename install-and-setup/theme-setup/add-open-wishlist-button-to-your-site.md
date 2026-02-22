---
description: >-
  This document explains the various methods to integrate the "Open Wishlist"
  button into your website. Our automatic installation typically handles the
  basic setup, but manual options are available.
icon: square-heart
---

# Add "Open Wishlist" Button to Your Site

### When to Use Manual Setup

Consider manual setup for the following scenarios:

* **Adding a second button to your mobile menu:** If you need more than one wishlist button, for example, one in your header and another specifically for mobile navigation.
* **Adding to older themes that don't support app blocks:** For themes that predate or do not fully support Shopify's app block functionality.
* **You prefer to add the code to your theme yourself:** For developers or users who want direct control over their theme's code.

### Installation Options

#### **Option 1: Using App Blocks (Recommended for Compatible Themes)**

If your theme supports Shopify's app blocks, this is the most straightforward and recommended method. App blocks allow for easy integration and management of app-related functionalities directly within the theme customizer.

For detailed instructions on adding app blocks to your header, please refer to our dedicated guide:

[Add App Blocks to Your Theme - Add App Block to Header](https://wishlist.nativeappco.com/install-and-setup/theme-setup/add-app-blocks-to-your-theme#add-app-block-to-header)

#### **Option 2: Manual HTML Element Integration**

You can manually add the "Open Wishlist" button anywhere on your site by inserting the following HTML element directly into your theme's Liquid files (e.g., `header.liquid`, `footer.liquid`, or any relevant section files).

This method provides full flexibility in terms of button placement.

**HTML:**

```
<open-wishlists-button role="button" data-primary="">
<svg xmlns="http://www.w3.org/2000/svg" width="26" height="24" fill="none"><path d="M20.583 22.75 13 17.333 5.417 22.75V5.417A2.167 2.167 0 0 1 7.583 3.25h10.834a2.167 2.167 0 0 1 2.166 2.167V22.75Z" stroke="currentColor"></path></svg>
<div class="wishlist-count-bubble"> </div>
</open-wishlists-button>
```

**Customizing the Icon:**

In the snippet above, the `<svg>` element represents the default wishlist icon. You have the flexibility to replace this SVG with your own custom wishlist icon or an image file to match your brand's aesthetics. Ensure that your replacement icon is appropriately sized and styled to fit within your design.
