# Business Rules — Taxi App

---

### BR-01 — Price is calculated before order confirmation

The system calculates the ride cost automatically based on route distance and the tariff of the selected vehicle category. The passenger sees the estimated price before confirming the order. Confirmation is not possible without displaying the price.

---

### BR-02 — Tariff depends on vehicle category

The system has multiple vehicle categories (e.g. Economy, Comfort, Business). Each category has its own tariff set by the administrator. The passenger selects a category before ordering and sees the corresponding price.

---

### BR-03 — Card payment is charged after order confirmation

If the passenger selected card payment, the funds are charged immediately after the passenger confirms the order. Cancellation after charging requires a separate refund procedure.

---

### BR-04 — Cash payment is recorded after ride completion

If the passenger selected cash, the system records the transaction as "paid in cash" only after the driver marks the ride as completed. Until then, the transaction has the status "pending payment".

---

### BR-05 — Driver cannot start a new ride while current ride is active

A driver can have only one active order at a time. The system does not send new ride requests to a driver until the status of their current ride is changed to "completed".

---

### BR-06 — Ride request is sent only to active drivers within search radius

The system sends a ride request only to drivers who: have "online" status enabled, are within the search radius from the pickup point, and have no active order. Drivers outside the radius or with "offline" status do not receive the request.

---

### BR-07 — Rating is available only after ride completion

The passenger can rate the driver, and the driver can rate the passenger, only after the ride has received "completed" status. Rating an incomplete or cancelled ride is not possible.

---

### BR-08 — Driver cannot start working without verification

A driver who has not been verified by the administrator cannot switch to "online" status or receive orders. The system blocks access to driver functions until the account is confirmed.

---

### BR-09 — Passenger cancellation after driver acceptance is recorded in the system

If the passenger cancels the ride after the driver has already accepted the order, the system records the cancellation and notifies the driver. Frequent cancellations by the passenger may affect their rating.

---

### BR-10 — Administrator cannot manually change ratings

Driver and passenger ratings are formed exclusively based on ratings left after completed rides. The administrator has no right to manually edit the numeric rating value. This protects the system from abuse.
