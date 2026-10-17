# Brasaland — Project Brief

**Status:** Discovery / initial framing  
**Last updated:** 2026-10-17  
**Decision status:** This document consolidates the company context and student interests. It does not represent an approved product scope, architecture, or delivery commitment.

## 1. Company overview

Brasaland is a grilled-food restaurant chain founded in 2008 in Medellín, Colombia. The company briefing describes 14 company-owned restaurants across Colombia and Florida, approximately 115 employees, and around USD 6 million in annual revenue. The brand aims to deliver consistent food quality, warm service, and fast kitchen operations across locations.

Headquarters are in Medellín, with a commercial and operations office in Miami. The briefing identifies Mariana Restrepo as CEO and Brasaland Digital as the internal team responsible for modernising the company’s tools, systems, and automation.

## 2. Business problem

Brasaland has grown into a two-country operation while continuing to rely on fragmented tools and largely location-by-location processes. The briefing identifies different POS systems in Colombia and Florida, spreadsheets and manual communications, limited consolidated data, and a lack of real-time operational visibility. Examples include ingredient orders made through WhatsApp or phone without inventory data, physical loyalty cards that do not produce useful customer data, and weekly PDF reporting that limits timely executive decisions.

These constraints make it difficult to maintain consistent operations, understand performance across locations, coordinate purchasing, and make decisions from current, shared information.

## 3. Direction and desired outcomes

The company briefing describes needs across several areas. These are **candidate outcomes to guide discovery**, not a prioritised or approved implementation scope:

- **Operations:** Improve visibility into sales and location performance; support inventory-aware ingredient ordering and operational alerts.
- **Procurement:** Consolidate purchasing information and track supplier relationships and price changes across both markets.
- **Marketing and customer experience:** Modernise digital ordering and loyalty, build a better understanding of customers, and explore relevant product recommendations.
- **People and culture:** Reduce manual HR administration and improve onboarding and HR metrics while accounting for both labour markets.
- **Training and quality:** Make recipes and training materials easier to find, maintain, and distribute consistently.
- **Technology and data:** Establish shared company data and API capabilities, connect location data, and support operational and executive reporting.
- **Executive direction:** Make cross-location and cross-market performance easier to understand and act on.

A sensible discovery-level principle is to prioritise reliable, well-defined operational data and workflows before depending on advanced analytics or AI. This is a recommendation for planning, not a stated company decision.

## 4. Student interests and exploratory AI concept

The student’s stated areas of interest are restaurant operations, marketing and digital experience, and training and quality standards (`company-choice.md`). Their exploratory AI concept is a menu-personalisation experience that could use a customer’s explicitly provided preferences and, optionally, order history to suggest suitable menu items.

The concept might be accessed through the website or app, including via a QR code, and could return a reduced set of menu options with a highlighted suggestion. The student also recognises that customers should be able to decline use of their order history and that staff assistance should remain available.

**This is an individual idea for exploration, not an approved Brasaland initiative or committed project scope.** Any future design would need to define consent, data minimisation, privacy and retention, reliable menu and allergen data, and a safe fallback. Recommendations must not treat AI output as a substitute for authoritative allergen information or staff guidance.

## 5. Initial constraints and considerations

- **Two markets:** Colombia and Florida introduce country-specific operating and labour contexts.
- **Currencies and languages:** The briefing calls out COP and USD, and Spanish and English as relevant considerations.
- **Fragmented systems:** POS systems differ by country; no internal API or consolidated data pipeline is described as currently available.
- **Operational consistency:** Any solution should support a consistent customer and kitchen experience across locations.
- **Data quality and timeliness:** Decisions and automation depend on dependable source data and clear ownership.
- **Privacy and safety:** Customer preferences, order history, and allergy or intolerance information require deliberate handling and appropriate human safeguards.

These are planning considerations derived from the briefing and student concept. They are not a completed technical or legal assessment.

## 6. Scope boundaries for this brief

This brief records the business context and frames possible outcomes. It does **not** select a first product, define MVP requirements, establish integrations, prescribe a technology stack, or assert that Brasaland has approved any of the department-level requests. Those decisions require further discovery and prioritisation.

## 7. Source material

- [`../CONTEXT.md`](../CONTEXT.md) — company briefing, current challenges, department needs, and operating context.
- [`../company-choice.md`](../company-choice.md) — student’s selection rationale, areas of interest, and exploratory menu-personalisation concept.
