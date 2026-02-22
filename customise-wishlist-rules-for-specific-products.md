---
description: >-
  Use Fish Wishlist's Tag Actions to customise the way the Add to Wishlist and
  Add to Cart buttons function.
icon: tag
---

# Customise Wishlist Rules for Specific Products



{% embed url="https://www.youtube.com/watch?v=TpIeVfmW51Q" %}



***

### Accessing Tag Actions

1. Open the Fish Wishlist app in your Shopify admin.
2. Navigate to the Settings page.
3. Scroll down until you reach the Tag Actions section.

***

### Available Action Types

There are three main categories of actions you can configure:

#### 1. Add to Cart Button Action

This overrides the behavior of the "Add to Cart" button inside the wishlist drawer.

* **Rename Label**: Change the text of the button (e.g., change "Add to Cart" to "Pre-order").
* **Disable Button**: Keeps the button visible but makes it unclickable.
* **Hide Button**: Removes the button entirely from the wishlist item.
* **Redirect after Click**: Send the user to a specific URL (like a collection page or a custom form) after they click the button.
* **Custom JavaScript**: For advanced users who want to trigger a custom script.

#### 2. Social Proof Widget Action

This affects the social proof notifications (e.g., "5 people have this in their wishlist") that appear on your product pages.

* Hide Widget: Use this to prevent the widget from showing on specific products, such as out-of-stock items or new arrivals where data might still be low.

#### 3. Wishlist Item Action

This controls elements of the wishlist item display on the product page or within the wishlist itself.

* **Hide Price**: Useful for "Price on Application" items or products where you wish to hide the cost until a specific tag is removed.

***

### How to Set Up an Action

#### Identify the Product Tag

In the Product Tag field, enter the specific tag you use in Shopify (e.g., `new`, `clearance`, or `pre-order`).

> Pro Tip: Use an asterisk `*` in the tag field to act as a wildcard. This will apply the action to all products in your store.

#### Select the Function

Choose the desired behavior from the dropdown menu (e.g., _Rename Label_).

#### Example: Renaming the Button for All Products

1. Under Add to Cart Button Action, enter `*` in the Product Tag field.
2. Select Rename Label from the dropdown.
3. Type your new text (e.g., "Buy Now") into the value field.
4. Click Save.
5. Open your wishlist drawer on your store to see the updated button label.

***

### Need Custom Functionality?

The Tag Actions system is flexible, and we frequently add new capabilities on a case-by-case basis. If you have a specific requirement—such as a different type of redirect or a unique button behavior not listed here—please [contact our support team](mailto:support@nativeappco.com) and we will be happy to assist you.
