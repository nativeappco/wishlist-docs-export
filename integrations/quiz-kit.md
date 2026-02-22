---
description: >-
  The Fish Wishlist and Quiz Kit integration allows quiz results to
  automatically populate a customer’s wishlist.
icon: trophy
---

# Quiz Kit

When a shopper completes a quiz, the recommended products from Quiz Kit are seamlessly added to their wishlist.

This integration is available to any store with both [**Fish Wishlist**](https://apps.shopify.com/fish-wishlist) and [**Quiz Kit**](https://apps.shopify.com/quiz-kit) installed.



***





<figure><img src="../.gitbook/assets/CleanShot 2025-08-19 at 21.08.29.gif" alt=""><figcaption></figcaption></figure>



***

### How it works

* A customer completes a quiz in Quiz Kit.
* Quiz Kit generates product recommendations.
* The recommended products are automatically added to the customer’s Fish Wishlist.

This makes it easier for customers to revisit their personalized quiz results later and take action directly from their wishlist.

***

### Setup Instructions



1. In your Shopify Admin, open the theme editor or theme code editor.
2. Locate the section where your Quiz Kit quiz is installed.
3. Create a new Liquid section (or edit an existing one under the quiz section).
4. Add the following script to the section:

```html
<script>
document.addEventListener('quizKitResultsPageLoaded', function (e) { 
  if(!("FishWishlist" in window)) return
  for(let recommendedProduct of e.detail.recommendedProducts) {
    let fishVariant = recommendedProduct.variants?.[0]
    if(!fishVariant) continue
    FishAPI.addToWishlist('WL1', {
      ...fishVariant,
      title: `${recommendedProduct.title}`,
      availableForSale: fishVariant.available_for_sale,
      featured_image: {
        src: fishVariant.image.src || recommendedProduct.image.src,
        src_small: fishVariant.image.src || recommendedProduct.image.src
      },
      price: {
        amount: parseFloat(fishVariant.price.replace(/[^0-9.]/g, ''))
      },
      compareAtPrice: {
        amount: fishVariant.compare_at_price
      }
    })
    FishWishlist.helpers.setCount()
    document.querySelector('wishlists-drawer').renderWishlistElements()
  }
}, false);
</script>
```

***

### That’s it!

Now, whenever a customer completes a quiz in Quiz Kit, their recommended products will automatically appear in their Fish Wishlist.

***

