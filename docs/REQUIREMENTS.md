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

**Priority:** Must
**Estimate** 4-6 hrs

---