---
icon: gift
---

# FoxSell Bundles

Stores using the [FoxSell Bundles](https://apps.shopify.com/foxsell-bundles-plus) app can use [Fish Wishlist](https://apps.shopify.com/fish-wishlist) to let customers add a bundle to their wishlist.

### Key Benefits

1. **Customers can save bundles for later**: If a customer users the bundle builder they can save the bundle to their wishlist and purchase later.
2. **Bundles appear as a single item in Wishlist**: Customers can build multiple bundles to their list and save for later.
3. **Add to Cart from Wishlist:** When a Bundle is added to cart from wishlist, it will work the same way as if you added directly from the FoxSell Bundles widget.<br>

### How it works

1. Before you start, you should have FoxSell Bundles and Fish Wishlist apps active on your store.
2. Add a snippet to your theme called `fish-foxsell.liquid`&#x20;
3. Paste this code into the file and save (it looks like a lot of code, but all you need to do is Copy and Paste).

```
<script>
  document.addEventListener("DOMContentLoaded", function() {
    if(!FishWishlist) return
    const bundleAtcButton = document.querySelector('.fsb__bundle-add-to-cart')
    if(!bundleAtcButton) return
    const wishlistButton = FishWishlist.helpers.insertPDPButton({
      cssSelector: ".fsb__bundle-add-to-cart",
      insertPosition: "insertbefore",
      classes: { pdpButton: "fsb__button" }
    })
    if(!wishlistButton) return
    const observer = new MutationObserver((mutationsList) => {
      for (const mutation of mutationsList) {
        if (mutation.attributeName === 'disabled') {
          // Sync disabled state
          if(wishlistButton.dataset.isAdded == "true") return
          if(bundleAtcButton.disabled) wishlistButton.classList.add("disabled")
          else wishlistButton.classList.remove("disabled");
        }
      }
    });
    if(wishlistButton.dataset.isAdded != "true") wishlistButton.classList.add("disabled")
    observer.observe(bundleAtcButton, { attributes: true });
  })
  document.addEventListener("fishwishlist:item-removed-from-wishlist", function(e, d) {
    let bundleWishlistButton = document.querySelector('wishlist-button-pdp.fsb__button')
    let isBundleDisabled = document.querySelector('.fsb__bundle-add-to-cart').disabled
    if(isBundleDisabled) bundleWishlistButton.classList.add("disabled")
    else bundleWishlistButton.classList.remove("disabled")
  })
  document.addEventListener("fishwishlist:item-added-to-wishlist", function(e, d) {
    if(!FishAPI) return
    let variant = e?.detail?.variant
    let wishlistId = e?.detail?.wishlistId
    const bundleSideBar = document.querySelector('.fsb__sidebar')
    if(!bundleSideBar) return
    const container = bundleSideBar.closest('section')
    const wishlistButton = container.querySelector(`wishlist-button-pdp[data-variant-id="${variant.id}"]`)
    if(!wishlistButton) return
    const selectedVariants = [
      ...Object.entries(bundleSideBar.bundleItems).map(([id, variantData]) => ({
        variantId: parseInt(id, 10),
        quantity: variantData.quantity,
        category: variantData.category,
        type: "product",
        properties: {}
      })), ...Object.entries(bundleSideBar.addOnItems).map(([id, variantData]) => ({
        variantId: parseInt(id, 10),
        quantity: variantData.quantity,
        type: "addOns",
        properties: {}
      }))
    ]
    
    const readableProperties = {};
    [...Object.entries(bundleSideBar.bundleItems), ...Object.entries(bundleSideBar.addOnItems)].forEach(([id, variantData]) => {
      let d = variantData.title;
      readableProperties[d] = readableProperties[d] ? `x${parseInt(readableProperties[d].replace("x", "")) + variantData.quantity}` : readableProperties[d] = `x${variantData.quantity}`
    })
    
    properties = {
      ...readableProperties,
      '__foxsell:dynamic_add_on_bundle_id': `${bundleId}_${Date.now()}`,
      '__foxsell:dynamic_add_on_bundle_items': JSON.stringify(selectedVariants),
      "__foxsell:original_bundle_price": 10000
    }
    FishAPI.addProperties(e.detail.wishlistId, e.detail.variant.id, properties)
  })
</script>
```

4. To activate the integration, insert  the following liquid tag to the theme template where FoxSell Bundles are active: `{% render 'fish-foxsell' %}`\
   If you are using Dawn theme, you can insert this at the bottom of `main-product.liquid`
5. After you Save, you will see the "Add to List" button appear within the FoxSell Bundle widget on your site, as follows:

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

For help with installation, email [fish@nativeappco.com](mailto:fish@nativeappco.com)&#x20;
