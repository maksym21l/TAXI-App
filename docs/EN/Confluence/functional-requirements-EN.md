# Functional Requirements — Taxi App

---

## Authentication

### FR-01 — Passenger Registration
The system must allow the passenger to register through the mobile app by providing name, phone number, and password. The phone number must be unique in the system.

### FR-02 — Driver Registration
The system must allow the driver to register through the mobile app by providing name, phone number, password, and vehicle details (make, model, license plate, category). The driver account is activated only after administrator verification.

### FR-03 — Login
The system must allow the passenger and driver to log in using phone number and password. If credentials are invalid, the system displays an error message. After successful login, the user is redirected to the main screen.

### FR-04 — Logout
The system must allow the user to end their session. After logout, access to the account without re-login is not possible.

---

## Passenger — Ride Ordering

### FR-05 — Enter Destination Address
The system must allow the passenger to enter pickup and destination addresses manually or select a point on the map. The system must validate the address and display an error if the address is not recognized.

### FR-06 — Select Vehicle Category
The system must display available vehicle categories (Economy, Comfort, Business) with the corresponding estimated ride price for each category. The passenger selects one category before confirming the order.

### FR-07 — Ride Price Calculation
The system must automatically calculate the ride cost based on route distance and the tariff of the selected category. The price is shown to the passenger before order confirmation.

### FR-08 — Order Confirmation
After selecting a category and reviewing the price, the passenger confirms the order. The system begins searching for an available driver. If card payment is selected — funds are charged at this moment.

### FR-09 — Driver Search
The system must automatically search for available drivers of the selected category within a radius from the pickup point. Requests are sent to drivers with "online" status and no active order. If no driver is found — the passenger receives a message suggesting to try again later or change the category.

### FR-10 — Real-Time Ride Tracking
After the driver accepts the order, the system must display the driver's current location and estimated arrival time on the map for the passenger. During the ride, the passenger sees the vehicle's live position.

### FR-11 — Passenger Order Cancellation
The passenger must be able to cancel the order before the driver arrives. The system records the cancellation, notifies the driver, and updates the ride status. For card payments, a refund procedure is initiated.

---

## Driver — Order Processing

### FR-12 — Online/Offline Status Toggle
The driver must be able to switch "online" and "offline" status. In "online" status the driver receives orders. In "offline" status — does not. Status change is only possible when there is no active order.

### FR-13 — Receive and Accept Order
The system must send the driver a ride request with details: pickup point, estimated distance and price. The driver can accept or reject the request. If rejected, the system searches for another driver.

### FR-14 — Navigation to Passenger and Destination
After accepting the order, the system must display the route to the pickup point, and after the ride starts — to the destination.

### FR-15 — Complete Ride
The driver must be able to mark the ride as completed after delivering the passenger. After completion, the system displays the final price and triggers the payment process (cash — recorded as received, card — already charged).

---

## Payment

### FR-16 — Select Payment Method
The passenger must be able to select a payment method when placing an order: card or cash.

### FR-17 — Card Payment Processing
When card is selected, the system must send transaction data to the payment provider after the passenger confirms the order. If the transaction is declined, the system displays an error and offers to choose another payment method or retry.

### FR-18 — Cash Payment Recording
When cash is selected, the system must record the transaction as "paid in cash" after the driver marks the ride as completed.

---

## Ratings

### FR-19 — Passenger Rates Driver
After ride completion, the system must prompt the passenger to rate the driver on a scale of 1 to 5 stars with an optional comment. The rating is saved and affects the driver's average score.

### FR-20 — Driver Rates Passenger
After ride completion, the system must allow the driver to rate the passenger on a scale of 1 to 5 stars. The rating is saved and affects the passenger's average score.

### FR-21 — Rating Display
The driver's rating must be shown to the passenger on the order details screen before confirming the ride. The passenger's rating must be visible to the driver when receiving a ride request.

---

## History

### FR-22 — Passenger Ride History
The system must store and display to the passenger a list of completed rides with details: date, route, cost, payment method, and driver rating.

### FR-23 — Driver Ride History
The system must store and display to the driver a list of completed rides with details: date, route, cost, and passenger rating.

---

## Administrator

### FR-24 — Driver Verification
The administrator must be able to view the list of drivers awaiting verification and approve or reject their registration. An approved driver gains access to app features.

### FR-25 — Tariff Management
The administrator must be able to set and update the tariff for each vehicle category. Tariff changes apply to new orders after saving.

### FR-26 — Ride Monitoring
The administrator must be able to view a list of active and completed rides with details: participants, route, status, and cost.

### FR-27 — User Management
The administrator must be able to block and unblock passenger and driver accounts. A blocked user cannot log into the system.

### FR-28 — Report Generation
The system must allow the administrator to generate reports for a selected period with data on number of rides, total revenue, and number of active drivers.
