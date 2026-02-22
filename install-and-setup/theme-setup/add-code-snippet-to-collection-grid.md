---
description: >-
  Insert our code snippet to your product grid item to add our wishlist buttons
  to your collection grid.
icon: heart-circle-plus
---

# Add code snippet to collection grid

Our snippet can be used with any search/filter provider such as Algolia, SearchSpring or Boost.

{% hint style="info" %}
This requires some edits to your theme code. If you need help, please [Contact Us](https://app.gitbook.com/u/ORl9VeaRJSOs4nsMpInXf0lzgvu2).
{% endhint %}

## Instructions

1. **Access Your Theme Files**:
   * In your Shopify admin, go to **Online Store** > **Themes**.
   * Find your published theme, and click **Actions** > **Edit Code**.
2. **Locate Product Grid Code**:
   * In the **Sections** or **Snippets** folder, open the file responsible for your product grid or product cards. Common file names include `product-grid-item.liquid`, `product-card.liquid`, or similar.
   * If you’re not sure which file it is, you can check your theme’s documentation or look for templates associated with collections or products.
3. **Insert the Wishlist Button Code**:
   * Within the code for the product grid item, locate a position where you want the wishlist button to appear.
   *   Paste the following code snippet within each product card section where you’d like the button:

       ```liquid
       <wishlist-button class="position-absolute top-right" data-variant-id="{{ card_product.variants | map: "id" | join: "," }}"></wishlist-button>
       ```
4. **Adjust Button Positioning** (Optional):
   * The `wishlist-button` class includes additional position attributes you can adjust to place the button inside the product card.
   * Replace `"top-right"` with one of the following options based on your desired placement:
     * **`top-right`**: Top right corner (default).
     * **`top-left`**: Top left corner.
     * **`bottom-right`**: Bottom right corner.
     * **`bottom-left`**: Bottom left corner.
5. **Save and Preview**:
   * Click **Save** after making changes.
   * Preview your store to ensure the wishlist button appears correctly within each product card.

This should set up the wishlist functionality for your theme!

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>



