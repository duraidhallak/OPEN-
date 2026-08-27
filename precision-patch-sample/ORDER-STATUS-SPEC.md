# Precision Patch — Order Status Specification

## Customer-visible lifecycle
- `ORDER_RECEIVED` — order submitted/received.
- `PROCESSING` — payment/order accepted and preparing for fulfillment.
- `SHIPPED` — carrier tracking assigned.
- `DELIVERED` — carrier reports delivery.
- `CANCELLED` — order cancelled before completion.
- `REFUNDED` — full refund completed.
- `PARTIALLY_REFUNDED` — partial refund completed.

## Internal operational states
- `NEW`
- `PAYMENT_AUTHORIZED`
- `PAYMENT_FAILED`
- `REVIEW`
- `READY_TO_FULFILL`
- `PICKING`
- `PACKED`
- `SHIPPED`
- `DELIVERED`
- `ADDRESS_HOLD`
- `FRAUD_HOLD`
- `INVENTORY_HOLD`
- `DAMAGE_REVIEW`
- `LOST_REVIEW`
- `FULFILLMENT_ERROR`
- `PRODUCT_COMPLAINT`
- `SAFETY_ESCALATION`
- `CANCELLED`
- `REFUND_PENDING`
- `REFUNDED`

## Required order record
Each production order should retain:
- order ID
- customer/account ID
- customer contact snapshot
- shipping-address snapshot
- SKU/product version
- quantity
- price/tax/shipping totals
- payment processor reference/token IDs only as appropriate
- merchant descriptor/version
- policy/consent version
- intake acknowledgement timestamp
- order creation/acceptance timestamps
- fulfillment status
- lot/batch shipped where applicable
- carrier/tracking
- cancellation/refund data
- support/escalation references

## Rules
- Customer-visible language should stay simple even when internal state is more specific.
- Never mark an order `SHIPPED` before carrier handoff/tracking is recorded.
- Never mark `REFUNDED` until refund is actually submitted/confirmed through the processor workflow.
- Holds should preserve the reason without exposing sensitive fraud logic to the customer.
- Every material state transition should create a timestamped audit event in production.

## Recommended customer account display
For each order show:
- order number
- order date
- product/quantity
- total
- current customer-visible status
- tracking when shipped
- links to Shipping and Returns policies
- support contact

## Notification events
- Order received
- Order accepted/processing
- Shipped
- Delivery exception if action is needed
- Delivered
- Cancelled
- Refund initiated/confirmed

## Payment activation dependency
This specification is backend-ready, but production order creation/payment capture remains blocked until processor/acquirer approval and the final product/fulfillment data are available.