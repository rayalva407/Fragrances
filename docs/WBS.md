# Work Breakdown Structure: Fragrances

**Author:** Raymundo Alva
**Date:** 10/21/2026
**Version:** 1.0
**Status:** Draft
**Related Docs:** [Project Charter](./PROJECT_CHARTER.md) | [Requirements](./REQUIREMENTS.md)

---

## 1. Overview

This document pulls from the epic and user stories from the Requirements document into actionable tasks. Each task has an ID (for Github Issue conversion), an estimate, and a dependancy note where relevant.

**Estimate legend:** Focused hours, learning-as-you-go.
**Task ID format:** `T-<epic>.<story>.<task>` - e.g., T-1.2.3

---

## 2. EP-1: Product Catalog (~40hrs)

### Foundation

| ID | Task | Est. | Depends On |
|----|------|------|------------|
| T-1.0.1 | Design Product entity (name, brand, description, family, notes) | 1.5 | - |
| T-1.0.2 | Design Variant entity (size, price, stock, FK to Product) | 1.5 | T-1.0.1 |
| T-1.0.3 | Write DB migrations | 2 | T-1.0.2 |
| T-1.0.4 | Create Spring Data repositories | 1 | T-1.0.3 |
| T-1.0.5 | Seed script: 20 - 30 products with variants and images | 5 | T-1.0.3 |

### US-1.1 Browse Products

| ID | Task | Est. |
|----|------|------|
| T-1.1.1 | GET /api/products (list and pagination) | 2 |
| T-1.1.2 | Catalog page UI (grid and pagination) | 4 |
| T-1.1.3 | Placeholder image handling | 1 |

### US-1.2 View Product Detail

| ID | Task | Est. |
|----|------|------|
| T-1.2.1 | GET /api/products/{id} (details and variants) | 1.5 |
| T-1.2.2 | Product detail page UI | 4 |

### US-1.3 Select Product Variant

| ID | Task | Est. |
|----|------|------|
| T-1.3.1 | Variant selector component (disable out-of-stock) | 3 |
| T-1.3.2 | Connect selected variant to "Add to Cart" action | 2 |

### US-1.4 Search Products

| ID | Task | Est. |
|----|------|------|
| T-1.4.1 | GET /api/products/search?q= (name and brand) | 2 |
| T-1.4.2 | Search bar UI + empty state | 1.5 |

### US - 1.5 Filter Products

| ID | Task | Est. |
|----|------|------|
| T-1.5.1 | GET /api/products/filter (family, brand, price) | 2.5 |
| T-1.5.2 | Filter panel UI and clear-all | 2.5 |

### Testing

| ID | Task | Est. |
|----|------|------|
| T-1.9.1 | API tests for EP-1 endpoints | 2 |
| T-1.9.2 | Manual QA: browse -> detail -> variant select | 2 |

---

## 3. EP-2: User Accounts (~22 hrs)

| ID | Task | Est. | Depends On |
|----|------|------|------------|
| T-2.1.1 | Configure Spring Security + JWT filter chain | 4 | — |
| T-2.1.2 | POST /api/auth/register (BCrypt hashing, validation) | 3 | T-2.1.1 |
| T-2.1.3 | Registration page UI + validation errors | 2 | T-2.1.2 |
| T-2.2.1 | POST /api/auth/login (issue JWT) | 2 | T-2.1.1 |
| T-2.2.2 | Login page UI + generic error handling | 2 | T-2.2.1 |
| T-2.2.3 | Token persistence (secure storage on client) | 2 | T-2.2.1 |
| T-2.3.1 | Logout (clear token, redirect) | 1 | T-2.2.1 |
| T-2.4.1 | GET /api/users/me + profile page UI | 3 | T-2.2.1 |
| T-2.9.1 | Protected-route guard (frontend + backend) | 2 | T-2.3.1 |
| T-2.9.2 | Auth tests | 2 | — |

---

## 4. EP-3: Shopping Cart  (~22 hrs)

| ID | Task | Est. | Depends On |
|----|------|------|------------|
| T-3.0.1 | Design Cart + CartItem entities (user or guest) | 2 | — |
| T-3.0.2 | Cart API (add / update / remove / get) | 4 | T-3.0.1 |
| T-3.1.1 | Add-to-cart UI + cart count badge | 3 | T-3.0.2 |
| T-3.2.1 | Cart page UI (line items, subtotal, delivery fee) | 3 | T-3.0.2 |
| T-3.3.1 | Quantity update UI + stock-cap validation | 3 | T-3.2.1 |
| T-3.4.1 | Remove item UI + empty state | 1 | T-3.2.1 |
| T-3.5.1 | Guest cart (local storage) | 2 | T-3.0.1 |
| T-3.5.2 | Cart merge on login | 3 | T-3.5.1, T-2.2.1 |
| T-3.9.1 | Cart tests | 2 | — |

---

## 5. EP-4: Checkout & Payment  (~25 hrs)

| ID | Task | Est. | Depends On |
|----|------|------|------------|
| T-4.1.1 | Delivery address form + field validation | 3 | T-3.2.1 |
| T-4.2.1 | Delivery zone config (zip list) | 1 | — |
| T-4.2.2 | Zone validation endpoint + checkout guard | 3 | T-4.2.1 |
| T-4.3.1 | Stripe account setup + test keys | 1 | — |
| T-4.3.2 | Integrate Stripe Checkout (backend session) | 5 | T-4.3.1 |
| T-4.3.3 | Wire "Pay" button → Stripe flow (frontend) | 3 | T-4.3.2 |
| T-4.3.4 | Stripe webhook / success handler → create Order | 4 | T-4.3.2 |
| T-4.4.1 | Order confirmation page | 3 | T-4.3.4 |
| T-4.9.1 | Checkout tests (success + decline cards) | 2 | — |

---

## 6. EP-5: Orders  (~12 hrs)

| ID | Task | Est. | Depends On |
|----|------|------|------------|
| T-5.0.1 | Design Order + OrderItem entities | 1.5 | T-3.0.1 |
| T-5.1.1 | GET /api/orders (current user) + history UI | 3.5 | T-5.0.1 |
| T-5.2.1 | GET /api/orders/{id} (authorize owner) + detail UI | 3.5 | T-5.1.1 |
| T-5.3.1 | Order status display (placed/delivered) | 1.5 | T-5.2.1 |
| T-5.9.1 | Order tests | 2 | — |

---

## 7. EP-6: Admin  (~20 hrs)

| ID | Task | Est. | Depends On |
|----|------|------|------------|
| T-6.0.1 | Admin role + seeded admin account | 2 | T-2.1.1 |
| T-6.1.1 | Product CRUD API (admin-only) | 4 | T-6.0.1 |
| T-6.1.2 | Admin product UI (list / create / edit / delete) | 5 | T-6.1.1 |
| T-6.2.1 | Variant management API + stock updates | 2 | T-6.1.1 |
| T-6.2.2 | Variant management UI | 3 | T-6.2.1 |
| T-6.3.1 | Update order status (admin) | 2 | T-5.0.1 |
| T-6.9.1 | Admin tests | 2 | — |

---

## 8. EP-7: Cross-Cutting: Infrastructure & Polish  (~20 hrs)

| ID | Task | Est. |
|----|------|------|
| T-7.1.1 | Project scaffolding (Spring Boot + RN Web via Expo) | 3 |
| T-7.0.2 | OpenAPI/Swagger setup | 2 |
| T-7.0.3 | Deploy backend (Render) | 3 |
| T-7.0.4 | Deploy frontend web | 3 |
| T-7.0.5 | Mobile build + verification | 4 |
| T-7.0.6 | README + architecture diagram + demo video | 5 |

---

## 9. Summary

| Epic | Est. Hours |
|------|-----------|
| EP-1 Product Catalog | 40 |
| EP-2 User Accounts | 22 |
| EP-3 Shopping Cart | 22 |
| EP-4 Checkout & Payment | 25 |
| EP-5 Orders | 12 |
| EP-6 Admin | 20 |
| EP-7 Cross-cutting | 20 |
| **Total** | **~161** |

This sits inside the charter's 155–230 hour estimate — as
expected, the low end assumes things go smoothly on first
attempt, which they rarely do. The higher end is the more
likely reality.

---

## 10. Suggested Build Order

1. **T-7.1** (scaffolding) → **EP-1 Foundation** → US-1.1 → US-1.2
2. **EP-2** (auth) → **EP-3** (cart, including US-3.5 guest cart)
3. **EP-4** (checkout — highest risk, do while you have momentum)
4. **EP-5** (orders) → **EP-6** (admin)
5. **T-7.2–T-7.6** (docs, deploy, polish) — interleave deploy early
   rather than leaving it all to the end

---

## 11. Notes

- Estimates assume learning-as-you-go; if you already know
  Spring Security or Stripe, reduce accordingly.
- Tasks are not strictly sequential — frontend work can
  begin against stubbed API responses.
- Convert each `T-x.y.z` row into a GitHub Issue and use a
  GitHub Project board to track status.
