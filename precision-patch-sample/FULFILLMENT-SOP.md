# Precision Patch — Fulfillment SOP

## Objective
Ship the correct finished product to the correct customer with traceable order, lot, and carrier records.

## Pre-fulfillment order states
`NEW` → `PAYMENT_AUTHORIZED` → `REVIEW` (only if needed) → `READY_TO_FULFILL`

Do not fulfill an order that is missing required payment authorization, shipping information, required acknowledgements, or inventory allocation.

## Pick/pack checklist
For each order:
1. Match order ID to customer/shipping record.
2. Match SKU and quantity.
3. Confirm product package is intact and unaltered.
4. Confirm unit is within expiration/shelf-life requirements.
5. Record lot/batch identifier where applicable.
6. Use approved shipper/packing material.
7. Print correct shipping label.
8. Final second check: name/address/SKU/quantity/lot.
9. Hand off to carrier.
10. Save tracking number and ship timestamp.

## Label/package integrity
- Do not cover, remove, black out, relabel over, or obscure legally required product information.
- Do not ship damaged, opened, contaminated, expired, or materially altered units.
- Any private-label/relabeling work must be completed under an approved final labeling plan before inventory enters sellable stock.

## Customer notifications
Recommended lifecycle:
- Order received.
- Payment accepted/order confirmed.
- Shipped + tracking.
- Delivery confirmation when carrier data supports it.
- Exception/delay message when intervention is required.

## Address issues
Before shipment: update only through an authenticated/support-controlled workflow with an audit record.
After carrier acceptance: do not promise rerouting. Use carrier-supported intercept/correction procedures when available.

## Damaged shipment
1. Ask customer for order number and photos of outer packaging and affected product.
2. Confirm tracking/delivery record.
3. Mark order `DAMAGE_REVIEW`.
4. Do not instruct customer to use compromised product.
5. Approve replacement/refund under published policy and authority limits.
6. Record reason and disposition.

## Lost shipment
1. Confirm carrier tracking status and delivery address.
2. Wait until the published carrier/merchant loss threshold is met.
3. Open carrier trace/claim when appropriate.
4. Mark `LOST_REVIEW`.
5. Replace/refund according to published policy.
6. Preserve carrier claim/reference number.

## Mis-shipment
If wrong SKU or quantity shipped:
1. Mark `FULFILLMENT_ERROR`.
2. Document photos/order record when useful.
3. Send correct replacement or refund.
4. Record root cause.

## Returns
- Opened/used wearable products should not return to sellable stock.
- Returned units must be quarantined until disposition is determined.
- Never restock a returned unit merely because outer packaging appears intact unless the final operating policy specifically permits it and product integrity is verified.

## Inventory controls
Production should track at minimum:
- SKU
- available quantity
- reserved quantity
- lot/batch
- received date
- expiration/shelf-life date where applicable
- inventory status (`SELLABLE`, `HOLD`, `QUARANTINE`, `EXPIRED`)

## Fulfillment owner gates
Still pending:
- supplier drop-ship vs merchant-controlled inventory
- physical fulfillment location
- carrier
- return address
- service-level target
- exact lot/expiration requirements from final product documentation