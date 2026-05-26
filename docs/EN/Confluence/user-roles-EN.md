# User Roles — Taxi App

---

## Roles Overview

| Role | Description |
|------|-------------|
| Customer | A person who wants to get from one place to another. Orders rides through the mobile app and pays by card or cash. |
| Driver | A person who delivers customers to their destination. Receives orders automatically through the mobile app. Must be verified by the administrator before starting work. |
| Administrator | Controls system operations. Verifies new drivers, manages tariffs, monitors active rides, and generates reports. |

---

## Role Descriptions

### Customer
The customer is the main end user of the mobile app. They open the app, enter a destination, select a vehicle category, confirm the order, and wait for a driver. The customer sees the price before confirming, tracks the driver on the map in real time, pays by card or cash, and rates the driver after the ride.

### Driver
The driver delivers customers to their destination. Before starting work, the driver must go through verification by the administrator — without this, they cannot receive orders. After verification, the driver switches to "online" status, receives automatic ride requests, accepts or rejects them, navigates to the passenger, completes the ride, and rates the customer.

### Administrator
The administrator manages the system through the web panel. They verify new driver registrations, set and update tariffs for each vehicle category, monitor active rides, block bad-faith users, and generate reports on rides and revenue. The administrator does not order or complete rides — they ensure the system operates correctly.

---

## Access by Role

| Feature | Customer | Driver | Administrator |
|---------|:--------:|:------:|:-------------:|
| Order a ride | ✅ | ❌ | ❌ |
| Accept and complete rides | ❌ | ✅ | ❌ |
| Rate after ride | ✅ | ✅ | ❌ |
| View ride history | ✅ | ✅ | ✅ |
| Verify drivers | ❌ | ❌ | ✅ |
| Manage tariffs | ❌ | ❌ | ✅ |
| Generate reports | ❌ | ❌ | ✅ |
| Block users | ❌ | ❌ | ✅ |
