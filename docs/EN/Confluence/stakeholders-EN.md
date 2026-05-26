# Stakeholders — Taxi App

---

## Stakeholder Table

| Stakeholder | Role | Interest | Influence |
|-------------|------|----------|-----------|
| Passenger | End user | Order a taxi quickly, know the price upfront, pay in a convenient way | High |
| Driver | Service operator | Receive orders automatically, have a clear interface, get paid on time | High |
| Administrator | System manager | Manage tariffs, verify drivers, monitor rides and generate reports | High |
| Support Team | Dispute resolution | Access ride and transaction history to handle complaints | Medium |
| Payment Provider | External service | Correct data transfer for processing card transactions | Medium |

---

## Stakeholder Descriptions

### Passenger
The passenger is the primary end user of the system. Previously they had to call a dispatcher or use alternative apps. The system allows the passenger to order a taxi in seconds, see the price and driver before the ride, and choose a convenient payment method — card or cash. After the ride, the passenger rates the driver and can view their ride history.

### Driver
The driver is the on-site service operator. Previously they received orders through a dispatcher or searched for passengers manually. The system sends orders automatically based on geolocation, allows accepting or rejecting requests, and keeps a record of completed rides. The driver is interested in a steady flow of orders and a simple interface. To start working, the driver goes through verification by the administrator.

### Administrator
The administrator manages the system through the web panel. They verify new drivers, set and update tariffs by vehicle category, block bad-faith users, monitor active rides, and generate reports. The administrator is the decision maker for the operational rules of the service.

### Support Team
The support team handles complaints from passengers and drivers — disputes about ride cost, payment issues, and behavior complaints. They need access to ride and transaction details. The support team does not manage the system but directly affects user loyalty.

### Payment Provider
An external service that processes card transactions. The system sends payment amount and card details to the provider, which confirms or rejects the transaction and returns the result. The reliability of the provider determines the success of all card payments in the system.
