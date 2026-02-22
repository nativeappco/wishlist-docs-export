---
description: >-
  Let your customers access their wishlist via a specific page on your site
  (rather than just via the slide out drawer). This feature is available by
  default on all stores.
icon: share-nodes
---

# Wishlist Landing Page

You can simply add this link anywhere on your site (or in your email templates) to point customers to their wishlist:

https://`<<yourstore.com>>`/apps/fish-wishlist/customer-wishlist/WL1  `(replace yourstore.com with your store's domain)`<br>

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

#### 🛠 Customization Tips:

* You can use  `card-product` or any custom snippet from your current theme.
* Adjust the grid layout, headings, and styling to better fit your brand.
* Use conditional logic to show different views for empty wishlists or logged-in users.
