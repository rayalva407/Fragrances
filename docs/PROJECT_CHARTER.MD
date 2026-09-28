# Project Charter: Fragrances 

**Author:** Raymundo Alva\
**Date:** 09/27/2026\
**Version:** 1.0\
**Status:** Approved

---

## 1. Executive Summary

Fragrances is an e-commerce application for browsing,
sampling, and purchasing fragrances. Application will be written 
in Java Spring Boot for REST API backend, a React Native 
frontend, and Stripe test-mode payment integration. This application targets
fragrance enthusiasts and people who want to discover new scents
at a lower cost than buying a full bottle. This app will allow for
product discovery, shopping cart, secure checkout, user accounts, and
tracking of orders for delivery. This product demonstrates full-stack
development, e-commerce domain modeling, and production-style deployment.

## 2. Problem Statement

Shopping for fragrances online can be frustrating: buyers don't have 
the option to sample fragrances, reviews can be very subjective, and buying
a full bottle blindly is extremely expensive. The existing markets don't allow
for a proper way of discovering new scents that is easy and user-friendly. There
is an exisiting market for a well-designed app that empowers users to find fragrances 
and try them affordably by offering decants and samples.

## 3. Project Goals & Objectives

- **Goal 1:** Build a functional MVP with user accounts, secure login and auth, 
product catalog, search and filter, shopping cart, and checkout by 02/28/27
- **Goal 2:** Implement authentication and order history
- **Goal 3:** Support product variants with at least three product types (samples and full bottles)
- **Goal 4:** Deploy to a public URL with a working demo (using test payments)
- **Goal 5:** Produce necessary documentation: README, architecture diagram, and demo walkthrough

## 4. Scope

### In-Scope (MVP)

**Product Catalog**
- Product listing with images, brand, description, and notes
- Product variants: sample (5ml), small size (30ml), full
  bottle (100ml)
- Search and filter by fragrance family, notes, brand, price
- Product detail page with size selector and per-variant stock

**User Accounts**
- Registration, login, logout
- Profile view with order history
- Persistent cart for logged-in users

**Cart & Checkout**
- Add/remove/update cart items
- Cart persists across sessions for logged-in users
- Checkout flow with shipping address entry
- Local delivery zone validation (zip code / region check)
- Stripe test-mode payment integration (Stripe Checkout or
  Payment Intents with test keys)
- Order confirmation page and email-style confirmation view

**Orders**
- Order history per user
- Order detail view with status (placed, delivered)
- Basic admin view for updating order status

**Admin**
- Simple product CRUD (create, read, update, delete)
- Variant-level inventory management
- Seed data script for 20–30 realistic products

### Out-of-Scope (v1):

- Real payment processing
- Product shipping outside local zone
- Multi-vendor / marketplace
- Native mobile app (Starting with React Native Web)
- Reviews, ratings, recommendations
- Subscriptions or loyalty rewards

## 5. Stakeholders

| Role | Name | Responsibility |
|------|------|----------------|
| Developer / PM | Raymundo Alva | Plan, design, build, document |
| Target end user | Fragrance enthusiasts, low budget shoppers, gift buyer | Feedback and validation |

## 6. High-Level Requirements

### Functional

- Users can browse, search and filter fragrances
- Users can view fragrance details for all products and variants including description and fragrance properties
- Users can add/remove fragrances from cart
- Users can create an account, log in, log out, and view order history
- Users can complete checkout flow with a delivery address
- Admin can add, edit, or remove fragrances in the product catalog

### Non-Functional

- Page loads in under two seconds
- Responsive design for both mobile and desktop
- Errors will be handled gracefully without disrupting the user experience
- Handle user data, login and logout securely

## 7. Success Criteria

The project is considered successful when:
- [ ] User should be able to create account, log in/log out, browse fragrances, manage shopping cart and checkout from beginning to end
- [ ] App is deployed and hould be publicly available
- [ ] Code is publicly available on Github with a README and instructions on how to set up
- [ ] Application needs to be seeded with at least 20 products to show realistic data
- [ ] Architecture diagrams and demo videos are available publicly

## 8. Constraints & Assumptions

### Constraints

- **Time:** 155–230 hours over 24–30 weeks at 6–8 hrs/week
- **Budget:** $0 for working MVP using Stripe test mode and free tiers only
- **Tech:** Spring Boot + React Native (Starting with web-first approach)
- **Hosting:** To be determined; For now thinking of Render free tiered account then AWS hosting

### Assumptions

- Hosting using a free-tier to start with should be sufficient
- No legal or compliance requirements

## 9. High-Level Risks

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Scope creep | High | High | Abide by strict in-scope requirements |
| Running out of time | Medium | High | Prioritize minimum requirements for MVP first |
| Product variant complexity | High | Medium | Create model with variants in mind from day 1 and seed simple data |
| React Native Web setup difficulties | Medium | High | Use Expo instead of drowing in configuration |
| AWS deployment | Medium | Medium | Deploy to a free-tiered solution like Render/Railway first then migrate to AWS later |
| Stripe integration difficulties | Low | Medium | Use Stripe Checkout (hosted) instead of custom forms |

## 10. Timeline & Milestones

| Milestone | Target Date | Week |
|-----------|-------------|------|
| Complete planning + charter | Oct 1, 2026 | Week 1 |
| Data model + product catalog API | Nov 5, 2026 | Week 6 |
| Frontend scaffold + browsing products | Dec 2, 2026 | Week 10 |
| Auth + cart working | Jan 6, 2027 | Week 15 |
| Checkout + Stripe test integration | Feb 3, 2027 | Week 19 |
| Orders + admin CRUD | Feb 24, 2027 | Week 22 |
| Web deployment | Mar 10, 2027 | Week 24 |
| Mobile build working | Mar 31, 2027 | Week 27 |
| Polish | Apr 21, 2027 | Week 30 |

## 11. Budget & Resources

- **Budget:** $0 (using free tiers only)
- **Backend:** Java Spring Boot
- **Frontend:** React Native + React Native Web
- **Database:** PostgreSQL
- **Payments:** Stripe test mode
- **Hosting:** Render then AWS later
- **Images:** Unsplash
- **Repo:** Github

## 12. Feasibility Summary

This project is feasible for a solo developer with the
following rationale:

- **Technical:** The chosen stack (Spring Boot, React Native,
  PostgreSQL) is well-documented with mature ecosystems.
  Variant-based product models are a standard e-commerce
  pattern. Stripe test mode removes payment compliance risk.
- **Economic:** Total cost is $0 using free tiers. No external
  funding required.
- **Operational:** Local delivery zone logic is config-driven;
  no logistics partnerships needed for v1.
- **Scheduling:** Estimated 155–230 hours over 24–30 weeks at
  6–8 hrs/week, which matches the developer's available time.

## 13. Related Documents

| Document | Location | Purpose |
|----------|----------|---------|
| Requirements | /docs/REQUIREMENTS.md | User stories & acceptance criteria |
| WBS | /docs/WBS.md | Task breakdown & schedule |
| Risk Register | /docs/RISK_REGISTER.md | Living risk log |
| Architecture | /docs/ARCHITECTURE.md | Tech design & schema |

## 14. Approval

**Prepared by:** Raymundo Alva
**Approved by:** Raymundo Alva
**Date:** 09/27/2026

## Appendix A: Technology Decisions

| Layer | Choice | Rationale |
|-------|--------|-----------|
| Backend | Java Spring Boot | Industry standard and great choice for e-commerce |
| Frontend | React Native + RN Web | Single codebase for both web and mobile with large community support |
| Database | PostgreSQL | Relational model that supports variants, orders and inventory data |
| Payments | Stripe (test mode) | Realistic integration and makes it easy to migrate to a real live mode later |
| Delivery | Local zone | Simpler than integrating carrier |
| Auth | JWT-based | Industry standard for REST APIs that works great for both web and mobile |

## Appendix B: Glossary

- **Variant:** A specific size/format of a fragrance product
  (e.g., 5ml sample, 30ml small, 100ml full bottle).
- **Local delivery zone:** A predefined geographic area
  (e.g., zip codes or region) eligible for delivery in v1.
- **MVP:** Minimum Viable Product — the smallest version that
  demonstrates the core value and flow.
- **Stripe test mode:** Stripe's sandbox environment using test
  API keys and test card numbers; no real money moves.
