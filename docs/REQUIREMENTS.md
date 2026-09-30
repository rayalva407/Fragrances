# Requirements: Fragrances

**Author:** Raymundo Alva\
**Date:** 09/28/2026\
**Version:** 1.0\
**Status:** Draft\
**Related:** [Project Charter](./PROJECT_CHARTER.md)

---

## 1. Overview

This document defines the functional and non-functional requirements for the Fragrances e-commerce application. Using the project charter, actionable user stories are created to provide a list of tasks that move development forward and track progress in a measurable way.

**Scope reference:** See project charter &sect;4 for a list of in-scope and out-of-scope items.

**Priority legend:**
- **Must** -- Required for MVP. Without it, project is incomplete
- **Should** -- Important but can be moved to later versions if time runs out
- **Nice** -- Optional. Only if time allows

**Estimate legend:** Focused hours, learning-as-you-go

---

## 2. Epics

| ID | Epic | Priority |
|----|------|----------|
| EP-1 | Product Catalog | Must |
| EP-2 | User Accounts | Must |
| EP-3 | Shopping Cart | Must |
| EP-4 | Checkout & Payment | Must |
| EP-5 | Orders | Must |
| EP-6 | Admin | Should |

---

## 3. User Stories

### EP-1: Product Catalog

---

**US-1.1 -- Browse Products**

As a shopper I should be able to browse the product catalog so that I can discover available fragrances.

**Acceptable Criteria:**

- From the catalog page, when the page loads, I should see a list of products with an image, brand and pricing for each product.
- If there are more than 12 products in the catalog, when the page loads, the products should be paginated or lazy loaded.
- If a product has no image, when it renders, then a placeholder image should be shown

**Priority:** Must\
**Estimate:** 4-6 hrs

---

**US-1.2 -- View Product Detail**

As a shopper, should be able to view a product's full details so I can make an informed choice and decide wether I want to buy the product.

**Acceptance Criteria:**

- If I'm on the catalog page, I should be able to click on an individual product and be taken to the product details page for that product.
- While on the detail page, I should be able to see the product's name, brand, description, fragrance notes, family, available variants with prices for each variant, and stock status.
- If the variant is out of stock, when the product renders, then the variant is visually disabled and cannot be clicked on or added to cart.

**Priority:** Must\
**Estimate:** 4-6 hrs

---

**US-1.3 --- Select Product Variant**

As a shopper, I should be able to click on the different variant types and choose sample, small, and full bottle sizes so that I can purchase the variant that fits my budget.

**Acceptance Criteria:**

- While on the product detail page, once the page loads, I should see all the available variants (5ml, 30ml, 100ml) with their corresponding prices and stock status.
- After selecting a variant, When I click "Add to Cart", the specific variant should be added to the cart (not the parent product).
- If a variant is out of stock, then it cannot be selected.

**Priority:** Must\
**Estimate:** 3-4 hrs

---

**US-1.4 --- Search Products**

- While on the catalog page, I should be able to type in a search box and see all products that match by name or brand.
- If my search returns no returns, then I should see an empty state and a customer-friendly message letting me know that no products match that search criteria.
- When clearing the search box, I should see all products in catalog are shown again.

**Priority:** Must\
**Estimate:** 3-4 hrs

---

**US-1.5 --- Filter Products**

As a shopper, I should be able to filter products by name, price, brand and other properties to narrow down the scents that I am interested in.

**Acceptance Criteria:**

- When on the catalog page, when selecting "Woody" from the family filter, then only the woody fragrances are shown.
- When multiple filters are applied, when clearing all filters, then all products should be shown.
- If no products match my filters, then I should see an empty state and a customer-friendly message and not an empty page

**Priority:** Must\
**Estimate:** 4-6 hrs

---

### EP-2: User Accounts

---
**US-2.1 --- Register Account**

As a new user, I want to create an account so that I save my cart and view order history.

**Acceptable Criteria:**

- While on the registration page, when I submit a valid username and password, my account should be successfully created and I should be automatically logged in.
- If I submit an email that already exists, I should see a clear error message.
- If I submit an invalid email or a weak password, I should see validation errors that clearly inform me what went wrong so that I can understand what changes to make before submission.

**Priority:** Must\
**Estimate:** 4-6 hrs

---

**US-2.2 --- Log In**

As a returning user, I should be able to log in so that I can see my order history and saved cart.

**Acceptable Criteria:**

- While on the login page, after submitting valid credentials, I should be successfully logged in and redirected to the catalog page
- When submitting invalid credentials, I should see a generic error ("Invalid username or password") to avoid hinting at which field was incorrect.
- While logged in, if I close and reopen the app, I should remain logged in (token persistance).

**Priority:** Must\
**Estimate:** 4-6 hrs

---

**US-2.3 --- Log Out**

As a logged-in user, I should be able to click on a log out button so that I can secure my account on shared devices.

**Acceptance Criteria:**

- If logged in, when clicking "Log Out", my session should end and I'm redirected to the catalog page.
- If I am logged out, I should not be able to access any protected pages, instead, I should be redirected to the login page.

**Priority:** Must\
**Estimate:** 1-2 hrs

---

**US-2.4 --- View Profile**

As a logged-in user I should be able to view my profile and see all of my account details.

**Acceptance Criteria:**

- While logged in, when I visit my profile I should see my name, email and a link to my order history.
- While not logged-in, trying to visit my profile should redirect to the login page.

**Priority:** Should\
**Estimate:** 2-3 hrs

---

### EP-3: Shopping Cart

---

**US-3.1 --- Add to Cart**

As a shopper, I should be able to add variants to my cart for purchase.

**Acceptance Criteria:**

- While on a product detail page with a variant selected, clicking "Add to Cart" should add the selected variant to the cart and cart count is updated.
- When adding a variant that is already present on the cart, the variant count should increase instead of creating a duplicate line
- If I'm not logged in, when I add to cart, the cart is stored locally and merged on login.

**Priority:** Must\
**Estimate** 4-6 hrs

---

**US-3.2 -- View Cart**

As a shopper, I should be able to review what I am going to buy by viewing my cart.

**Acceptance Criteria:**
- If there are items in my cart, when I open the cart, I should be able to see each item's name, image, variant, quantity, price and cart total.
- If the cart is empty, then I should be able to see an empty state with a link redirecting me to the catalog.
- If I'm on the cart page, I should be able to see a subtotal and the estimated delivery fee.

**Priority:** Must\
**Estimate:** 3-5 hrs

---

**US-3.3 -- Update Cart Quantity**

As a shopper, I should be able to change the quantity of items in order to purchase a specific amount for an item.

**Acceptance Criteria:**

- If I'm in my cart, when increaing the quantity of an item, then the line total and the cart subtotal should update.
- If I decrease the quantity to zero, the item should be removed from the cart completely.
- If I try to add a quantity that is over the item's current stock, then I should see an error showing that the item is capped at the stock amount.

**Priority:** Must\
**Estimate:** 3-4 hours

---

**US-3.4 -- Remove from Cart**

As a shopper, want to remove items so that I can exclude unwanted items.

**Acceptance Criteria:**

- If I'm in my cart, when clicking remove on an item, the item should be deleted and the subtotal should update.
- If I remove the last item, then the screen should update to the empty state

**Priority:** Must\
**Estimate:** 1-2 hrs

---

**US-3.5 -- Persisten Cart**

As a logged-in user, I want my cart to persists across sessions so that I don't lose my cart items when logging in/out of my account or closing and reopening the app.

**Acceptance Criteria:**

- If I'm logged and I have items in my cart, when I close and reopen the app, my cart should keep all items and remain unchanged.
- If I'm not logged in and have a cart (guest user), when I log in, the guest cart should merge into my logged-in account cart.

**Priority:** Should\
**Estimate:** 4-6 hrs

---

### EP-4: Checkout & Payment

---

**US-4.1 -- Enter Delivery Address**

As a shopper, I want to enter my delivery address so that my order can be delivered to me.

**Acceptance Criteria:**

- If I'm in checkout page, when I enter my delivery address, the address fields should include street, city, state, and zip, and should be validated.
- If the zip code I enter is outside of the local delivery area then I should get a message saying "Delivery is not available in your area" and I am unable to checkout.

**Priority:** Must\
**Estimate:** 4-6 hrs

---

**US-4.2 -- Validate Delivery Zone**

As the system, I want to validate that address is within the delivery zone so that I only accept valid orders.

**Acceptance Criteria:**

- Given a list of eligible zip codes, when a user enters an eligible zip code, then the checkout continues.
- When a user enters an ineligible zip code, then the checkout is blocked and a clear message is displayed.
- Given the zip code list is config-based, then I can update the list without changing code.

**Priority:** Must\
**Estimate:** 3-4 hrs

---

**US-4.3 -- Pay with Stripe**

As a shopper, I want to be able to pay with a credit/debit card so that I can conveniently complete my purchase.

**Acceptance Criteria:**

- Given that I'm in checkout with a valid cart and address, when I click "Pay", I am redirected to a Stripe payment flow.
- Given that I provide a Stripe test card, then my payment is successful and I'm redirected to confirmation page.
- Given that I provide a decline test card, then my payment is unsuccessful and I'm given a clear message that my payment did not complete and redirected to retry.
- Given that the payment succeeded, then an order should be created and stored in a database with a "placed" status.

**Priority:** Must\
**Estimate:** 8-12 hrs

---

**US-4.4 -- Order Confirmation:**

As a shopper, I want to see a confirmation once my order has been placed so that I know that my order has been taken.

**Acceptance Criteria:**

- Given that my payment is complete, I am redirected to a page that shows a confirmation page with an order number, items ordered, total amount and delivery address.
- Given that I'm on the confirmation page, I am shown a link to navigate to the order history.

**Priority:** Must\
**Estimate:** 3-4 hrs

---

### EP-5: Orders

---

**US-5.1 -- View Order History**

As a logged-in user, I want to view past orders so that I can reorder and review my purchases.

**Acceptance Criteria:**

- While logged in, after visiting the order history page, I should see a list of my previous orders from newest to oldest with a date, total and status.
- Given I don't have any orders, I should see an empty state with a friendly message.

**Priority:** Must\
**Estimate:** 3-4 hrs

**US-5.2 -- View Order Details**

As a logged-in user, I want to be able to select a single order from order history so that I can review what I previously bought.

**Acceptance Criteria:**

- Given I'm on the order history page, I should be able to select one single order and be redirected to the order details page where I can see variant details, quantities, items, totals and delivery address.
- Given I try to view other user's order, my access should be denied.

**Priority:** Must\
**Estimate:** 3-4 hrs

**US-5.3 -- Order Status**

**Acceptance Criteria:**
- As a shopper, I should be able to see my order status so that I know if it has been delivered.
- Given that the status is updated, then the shopper sees the changes when page refreshes.

**Priority:** Should\
**Estimate:** 2-3 hrs

---

### EP-6: Admin

---

**US-6.1 -- Admin Product CRUD**

As an admin, I want to add, view, update and delete products so that I can maintain the catalog.

**Acceptance Criteria:**

- Given I'm an admin, when I create a product, then that product should immediately show on the storefront for all users.
- Given I edit a product, when I edit that product, then those changes should be visible on the storefront for all users.
- Given I delete a product, when that product has been deleted, then the product should no longer show on the storefront, but it should still show on previous orders.

**Priority:** Should\
**Estimate:** 6-8 hrs

---

**US-6.2 -- Manage Variants**

As an admin, I want to manage product variants (size, stock, price) so that the inventory is accurate.

**Acceptance Criteria:**

- Given I'm editing a product, when adding a variant, then the variant should be available for purchase.
- Given I update the product stock, when the stock amount is changes, then the change should reflect on the storefront immediately.
- Given the stock reaches zero, then the variant should show as out of stock.

**Priority:** Should\
**Estimate:** 4-6 hrs

---

**US-6.3 -- Update Order Status**

As an admin, I want to change the order status to delivered so that the customer sees an accurate order status.

**Acceptance Criteria:**

- Given I change an order status to delivered, then the customer should be notified and also see the up-to-date status on their end.

**Priority:** Should\
**Estimate:** 2-3 hrs

---

**US-6.4 -- Seed Data**

- As a developer, I want to use a script that loads realistic product data so that the application looks like a production-ready application.

**Acceptance Criteria:**

- Given an empty database, when I run the seed script, I should see up to 30 fragrances with variants, images and metadata are created and saved to the database.
- Given seed data exists, then the catalog should render like a real-world application without adding data manually.

**Priority:** Must\
**Estimate:** 4-6 hrs

---
