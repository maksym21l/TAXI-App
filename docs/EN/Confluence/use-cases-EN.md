# Use Case Specification — Taxi App

---

# UC-01 — Passenger Ride Ordering

| Field | Description |
|-------|-------------|
| Use Case ID | UC-01 |
| Use Case Name | Passenger Ride Ordering |
| Primary Actor | Passenger |
| Secondary Actors | Driver, System, Payment Provider |
| Scope | Taxi App |
| Level | User Goal |

## Goal

Allow the passenger to create a ride order, get matched with a driver, complete the ride, pay, and rate the driver.

## Preconditions

- Passenger is registered and logged into the system
- At least one active driver of the required category exists in the system
- System is available

## Trigger

The passenger opens the app and wants to order a ride.

## Main Success Scenario

1. Passenger opens the mobile app
2. Passenger enters the destination address
3. System validates the address and displays the route on the map
4. System displays available vehicle categories with estimated prices
5. Passenger selects a vehicle category
6. Passenger selects a payment method (card or cash)
7. Passenger confirms the order
8. If card payment — system sends the transaction to the payment provider and charges funds
9. System searches for an available driver of the selected category
10. System sends a request to the driver
11. Driver accepts the order
12. System displays driver details to the passenger: name, rating, car make, license plate
13. Passenger tracks the driver's movement on the map
14. Driver arrives at the pickup point
15. Passenger gets in the car — ride starts
16. Driver delivers passenger to the destination
17. Driver completes the ride in the app
18. System displays the final ride cost
19. If cash payment — passenger pays the driver, system records the payment
20. System prompts passenger to rate the driver
21. Passenger gives a rating from 1 to 5 stars and optionally leaves a comment
22. Ride successfully completed

## Postconditions

### Success Postconditions
- Ride is saved in the system with "completed" status
- Transaction is processed and saved
- Driver rating is updated (if rating was given)
- Ride appears in both passenger and driver history

### Failure Postconditions
- Ride is not created or is cancelled
- Transaction is not processed
- Ride status is "cancelled" or "error"

---

## Alternative Flows

### A1 — Invalid Address

1. Passenger enters destination address
2. System cannot recognize the address
3. Message is displayed: `Address not found`
4. Passenger enters a new address
5. Process returns to address input step

### A2 — No Available Drivers

1. System searches for drivers of the selected category
2. No drivers are found
3. Message is displayed: `No drivers nearby. Try again later or select a different category`
4. Passenger can change category or close the app

### A3 — Driver Rejects Request

1. System sends a request to the driver
2. Driver rejects the request
3. System searches for another available driver
4. Process returns to driver search step

### A4 — Passenger Cancels Before Driver Arrives

1. Passenger taps "Cancel"
2. System cancels the order
3. Driver receives a cancellation notification
4. If card payment — refund is initiated
5. Ride is saved with "cancelled" status

### A5 — Passenger Skips Driver Rating

1. System prompts passenger to rate the driver
2. Passenger closes the rating screen
3. Ride is completed without a rating

---

## Exception Flows

### E1 — Card Transaction Declined

1. System sends transaction data to the payment provider
2. Provider declines the transaction
3. Message is displayed: `Payment failed`
4. Passenger can retry or switch to cash

### E2 — Driver Cancels After Accepting

1. Driver cancels the accepted order
2. System notifies the passenger
3. If card payment — refund is initiated
4. System searches for another driver
5. Process returns to driver search step

### E3 — System Unavailable

1. System becomes unavailable at any step
2. Message is displayed: `Service temporarily unavailable. Please try again later`
3. Process stops

---

# UC-02 — Driver Order Processing

| Field | Description |
|-------|-------------|
| Use Case ID | UC-02 |
| Use Case Name | Driver Order Processing |
| Primary Actor | Driver |
| Secondary Actors | Passenger, System |
| Scope | Taxi App |
| Level | User Goal |

## Goal

Allow the driver to receive an order, deliver the passenger to the destination, and complete the ride.

## Preconditions

- Driver is registered and verified by the administrator
- Driver is logged in and has "online" status
- Driver has no active orders

## Trigger

The system identifies the driver as the nearest available and sends them a ride request.

## Main Success Scenario

1. Driver receives a ride request
2. System displays order details: pickup point, estimated distance, price, passenger rating
3. Driver accepts the order
4. System displays route to the pickup point
5. Driver heads to the passenger
6. Driver arrives at the pickup point
7. Passenger gets in the car
8. Driver starts the ride in the app
9. System displays route to the destination
10. Driver delivers the passenger
11. Driver marks the ride as completed in the app
12. System displays the final price and payment method
13. If cash — driver receives payment from the passenger
14. System prompts the driver to rate the passenger
15. Driver gives a rating from 1 to 5 stars
16. Ride is saved. Driver returns to "online" status and is ready for new orders

## Postconditions

### Success Postconditions
- Ride is saved with "completed" status
- Passenger rating is updated
- Ride appears in driver history

### Failure Postconditions
- Ride is cancelled or incomplete
- Ride status is "cancelled"

---

## Alternative Flows

### A1 — Driver Rejects the Order

1. Driver receives the request
2. Driver taps "Reject"
3. System searches for another driver
4. Driver remains in "online" status

### A2 — Driver Cancels After Accepting

1. Driver accepted the order but must cancel
2. Driver taps "Cancel"
3. System notifies the passenger
4. System searches for another driver for the passenger
5. Driver returns to "online" status

### A3 — Driver Skips Passenger Rating

1. System prompts driver to rate the passenger
2. Driver closes the rating screen
3. Ride is completed without a passenger rating

---

## Exception Flows

### E1 — System Unavailable During Ride

1. System becomes unavailable during an active ride
2. Navigation in the app stops updating
3. Driver completes the ride using the last known route
4. After system recovery, the ride is synchronized

---

# UC-03 — Driver Verification by Administrator

| Field | Description |
|-------|-------------|
| Use Case ID | UC-03 |
| Use Case Name | Driver Verification by Administrator |
| Primary Actor | Administrator |
| Secondary Actors | Driver, System |
| Scope | Taxi App — Admin Panel |
| Level | User Goal |

## Goal

Allow the administrator to review a new driver's details and grant or deny access to the system.

## Preconditions

- Administrator is logged into the web panel
- Driver is registered in the system and awaiting verification

## Trigger

Driver has completed registration. Administrator opens the driver verification list.

## Main Success Scenario

1. Administrator opens the "Drivers Pending Verification" section
2. System displays a list of drivers with "pending review" status
3. Administrator selects a driver from the list
4. System displays driver details: name, phone number, vehicle data (make, model, license plate, category)
5. Administrator reviews the details
6. Administrator clicks "Approve"
7. System changes driver status to "verified"
8. Driver receives a notification that their account has been approved
9. Driver can switch to "online" status and start receiving orders

## Postconditions

### Success Postconditions
- Driver status changed to "verified"
- Driver has access to app features

### Failure Postconditions
- Driver status remains "rejected"
- Driver cannot use the app

---

## Alternative Flows

### A1 — Administrator Rejects Driver

1. Administrator reviews the details
2. Details are incorrect or incomplete
3. Administrator clicks "Reject"
4. System changes driver status to "rejected"
5. Driver receives a rejection notification

---

## Exception Flows

### E1 — Status Save Error

1. Administrator approves or rejects the driver
2. System cannot save the status change
3. Error message is displayed
4. Driver status is not changed
5. Administrator can retry the action
