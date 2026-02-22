---
description: >-
  Customers can share their wishlist with friends using our share feature. Store
  owners can customise this feature using our advanced editor.
icon: share-nodes
---

# Wishlist Sharing

### Turn on Wishlist Sharing

Wishlist Sharing can be turned from the [Settings](https://admin.shopify.com/apps/fish-wishlist/app/settings) tab:

<figure><img src=".gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

### How It Works

Fish Wishlist uses a **two-step sharing flow** by default:

1.  **Step 1 - Customer Shares Wishlist**<br>

    * When a user clicks the **Share Wishlist** button, the wishlist is marked public by generating a **metaobject** and a **public link** to the wishlist page.

    <div data-full-width="false"><figure><img src=".gitbook/assets/CleanShot 2025-06-16 at 20.20.34.gif" alt="" width="324"><figcaption></figcaption></figure></div>
2. **Step 2 - Share the Link**
   * A **share popup** is triggered with the link that can be copied or shared via social/email.
3. **Unsharing the Wishlist**
   * If the user decides to revoke access, they can click **Unshare Wishlist**, which marks the wishlist as private and invalidates the public URL.



***

### Accessing the Custom Page Editor (advanced)

<figure><img src=".gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

Fish Wishlist provides a **hidden editor** for advanced users. You can manage your wishlist page directly through the following link:

➡️ [Wishlist Page Editor (Advanced Access)](https://admin.shopify.com/apps/fish-wishlist/app/pages)

> **Note:** This link is hidden in your app admin. Use it only if you’re familiar with theme development and advanced customization.

### Editing the Shared Wishlist Page Template

The shared wishlist page uses a **generic grid-based layout**, which is designed to work across Shopify themes.

You can fully customize this page via the hidden editor and insert any theme-compatible code. Below is a sample template for rendering the shared wishlist using Shopify’s Dawn theme structure.

#### Sample Code for Dawn Theme:

```liquid
{{ 'component-card.css' | asset_url | stylesheet_tag }}
<div class="collection page-width">
    <h2> {{ wishlist.title | default: "Shared wishlist" }}</h2>
    <ul class="grid product-grid grid--2-col-tablet-down grid--4-col-desktop"> 
      {% for item in wishlist.items.value %}
      <li class="grid__item">
        {% render 'card-product',
          card_product: item.product,
          media_aspect_ratio: "adapt",
          image_shape: "default",
          show_secondary_image: true,
          show_vendor: true,
          show_rating: true,
          skip_styles: false,
          section_id: section.id,
          quick_add: false
        %}
        </li>
      {% endfor %}
    </ul>
</div>

```

#### Adding a "Share button" to your Wishlist page

To allow your customers to easily share their wishlists, you can add a dedicated "Share button" to their wishlist page. This button will generate a shareable link to their public wishlist.

You can implement this feature by adding the following code snippet to your wishlist page template:

Code snippet

```
{% if metadata.sharedWishlist.handle != blank %}
<fish-wishlist-share-button
  data-url="https://<MYSTORE.COM>/apps/fish-wishlist/shared-wishlist/{{ metadata.sharedWishlist.handle }}"
  data-title="{{ metadata.sharedWishlist.title }}"
  title="{{ metadata.sharedWishlist.title }}">
  <button class="fish-wishlist-share-button fish-wishlist-button--link button--share">
    <svg width="13" height="12" viewBox="0 0 13 12" class="icon icon-share" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden="true" focusable="false"> <path d="M1.625 8.125V10.2917C1.625 10.579 1.73914 10.8545 1.9423 11.0577C2.14547 11.2609 2.42102 11.375 2.70833 11.375H10.2917C10.579 11.375 10.8545 11.2609 11.0577 11.0577C11.2609 10.8545 11.375 10.579 11.375 10.2917V8.125" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round"></path> <path fill-rule="evenodd" clip-rule="evenodd" d="M6.14775 1.27137C6.34301 1.0761 6.65959 1.0761 6.85485 1.27137L9.56319 3.9797C9.75845 4.17496 9.75845 4.49154 9.56319 4.6868C9.36793 4.88207 9.05135 4.88207 8.85609 4.6868L6.5013 2.33203L4.14652 4.6868C3.95126 4.88207 3.63468 4.88207 3.43942 4.6868C3.24415 4.49154 3.24415 4.17496 3.43942 3.9797L6.14775 1.27137Z" fill="currentColor"></path> <path fill-rule="evenodd" clip-rule="evenodd" d="M6.5 1.125C6.77614 1.125 7 1.34886 7 1.625V8.125C7 8.40114 6.77614 8.625 6.5 8.625C6.22386 8.625 6 8.40114 6 8.125V1.625C6 1.34886 6.22386 1.125 6.5 1.125Z" fill="currentColor"></path> </svg>
    <span>Send Share Link</span>
  </button>
  <button class="fish-wishlist-share-button button--copy">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="4 3 12 14"><path fill-rule="evenodd" d="M6.515 4.75a2 2 0 0 1 1.985-1.75h3a2 2 0 0 1 1.985 1.75h.265a2.25 2.25 0 0 1 2.25 2.25v7.75a2.25 2.25 0 0 1-2.25 2.25h-7.5a2.25 2.25 0 0 1-2.25-2.25v-7.75a2.25 2.25 0 0 1 2.25-2.25h.265Zm1.985-.25h3a.5.5 0 0 1 .5.5v1a.5.5 0 0 1-.5.5h-3a.5.5 0 0 1-.5-.5v-1a.5.5 0 0 1 .5-.5Zm-1.987 1.73.002.02h-.265a.75.75 0 0 0-.75.75v7.75c0 .414.336.75.75.75h7.5a.75.75 0 0 0 .75-.75v-7.75a.75.75 0 0 0-.75-.75h-.265a2 2 0 0 1-1.985 1.75h-3a2 2 0 0 1-1.987-1.77Z"></path></svg>
    <span>Copy Share Link</span>
  </button>
</fish-wishlist-share-button>
{% endif %}
```

**Important Note:** These share buttons will only be visible to a customer if they have previously enabled the shared wishlist feature using the dedicated button within the wishlist drawer.

#### 🛠 Customization Tips:

* You can use  `card-product` or any custom snippet from your current theme.
* Adjust the grid layout, headings, and styling to better fit your brand.
* Use conditional logic to show different views for empty wishlists or logged-in users.
