# Vision & Scope — Taxi App

---

## Vision

The goal of the system is to automate taxi ordering across multiple cities through a mobile application. Instead of phone calls and manual dispatching, passengers order a ride in a few taps, the system automatically matches the nearest available driver, calculates the price, and processes payment.

The key success metric is **driver waiting time**. Fast arrival builds trust and brings passengers back. Target at launch: average waiting time no more than 5 minutes within the city.

---

## System Components

| Component | Users | Purpose |
|-----------|-------|---------|
| Mobile app (passenger) | Passenger | Order rides, pay, view ride history, rate driver |
| Mobile app (driver) | Driver | Accept and complete rides, navigation, rate passenger |
| Admin web panel | Administrator | User management, tariff settings, reporting |

---

## Scope

### What is included in this version

| # | Feature | Component |
|---|---------|-----------|
| 1 | Registration and login for passenger and driver | Mobile app |
| 2 | Ride request with vehicle category selection | Passenger app |
| 3 | Automatic ride price calculation | System |
| 4 | Search for nearest available driver | System |
| 5 | Driver accepts or rejects ride request | Driver app |
| 6 | Real-time ride tracking | Both apps |
| 7 | Card payment (charged after ride confirmation) | System |
| 8 | Cash payment (recorded after ride completion) | System |
| 9 | Mutual rating — passenger rates driver, driver rates passenger | Both apps |
| 10 | Ride history | Both apps |
| 11 | Driver verification by administrator | Admin panel |
| 12 | Tariff management by vehicle category | Admin panel |
| 13 | Ride monitoring and reports | Admin panel |

### What is NOT included in this version

| # | Feature | Reason |
|---|---------|--------|
| 1 | Scheduled rides in advance | Complex queue logic — planned for next version |
| 2 | Corporate accounts | Separate business model — out of MVP scope |
| 3 | Promo codes and discounts | Marketing module — planned for next version |
| 4 | In-app chat between passenger and driver | Replaced by phone call through the app |
| 5 | Automatic driver document verification | Requires third-party integration — next version |

---

## Future Improvements

In future versions the system could include:
- Automatic driver document verification
- Promo codes and referral program
- Scheduled ride booking
- Corporate accounts with separate reporting
- In-app chat between passenger and driver
