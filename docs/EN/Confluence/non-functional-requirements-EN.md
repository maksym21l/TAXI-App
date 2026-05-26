# Non-Functional Requirements — Taxi App

---

### NFR-01 — Performance

**Requirement:** Driver search time after order confirmation must not exceed 2 seconds.

**Why:** The passenger has just confirmed the order and is waiting for a system response. A delay of more than 2 seconds creates the impression that the system has frozen and reduces trust. Fast response is critical for the first impression of the service.

---

### NFR-02 — Availability

**Requirement:** System uptime must be at least 99% per month. During peak hours (07:00–09:00 and 17:00–20:00) the system must be available 100%.

**Why:** If the system is unavailable in the morning or evening, passengers cannot get to work or home. For a transportation service, peak hours are critical — a single outage during this time means the loss of hundreds of orders and significant reputational damage.

---

### NFR-03 — Security

**Requirement:** All card transactions must be transmitted over a secure channel (HTTPS). User passwords must be stored in hashed form. Access to the admin panel is only possible after authentication.

**Why:** The system processes passenger financial data. A leak of payment information or unauthorized access to the admin panel are critical risks that can lead to financial losses and legal liability.

---

### NFR-04 — Scalability

**Requirement:** The system must support up to 500 simultaneous active rides without performance degradation.

**Why:** During peak hours across multiple cities there can be a large number of active rides simultaneously. When load is exceeded, driver geolocation updates begin to lag — the passenger sees an outdated vehicle position, which destroys trust in the service.

---

### NFR-05 — Usability

**Requirement:** The passenger must be able to place an order in no more than 4 steps from opening the app to confirmation.

**Why:** More steps means a higher chance of drop-off. 4 steps (open → enter address → select category → confirm) is the minimum required flow that cannot be reduced without losing functionality. Every extra screen increases the abandonment rate.

---

### NFR-06 — Real-Time Geolocation Updates

**Requirement:** The driver's position on the passenger's map must update at least once every 3 seconds during waiting and the ride.

**Why:** If the driver marker on the map does not move, the passenger does not know where the vehicle is or whether it is moving at all. Updates every 3 seconds provide a sufficient sense of real-time movement without excessive load on the server and phone battery.
