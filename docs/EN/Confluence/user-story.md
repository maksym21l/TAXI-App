# User Stories & Acceptance Criteria

---

# Registration & Authentication

## US-01 Customer Registration

### User Story
As a customer,  
I want a simple registration process,  
so that I can start using the taxi service quickly.

### Acceptance Criteria
- Customer can open registration form
- Customer can enter email and password
- System validates entered data
- Customer account is created successfully
- Customer receives confirmation message

---

## US-02 Driver Registration

### User Story
As a driver,  
I want a fast registration process,  
so that I can start working quickly.

### Acceptance Criteria
- Driver can complete registration form
- Driver can enter vehicle information
- System validates driver data
- Driver account is created successfully
- Driver can access driver dashboard

---

## US-03 Login

### User Story
As a customer,  
I want to log in using email and password,  
so that I can request taxi rides.

### Acceptance Criteria
- User can enter email and password
- System validates credentials
- User is redirected after successful login
- Error message is shown for invalid credentials
- User session is created successfully

---

## US-04 Stay Logged In

### User Story
As a user,  
I want to stay logged in on my device,  
so that I do not need to enter credentials every time.

### Acceptance Criteria
- System remembers authorized user
- User stays logged in after app restart
- Session expires after logout
- Unauthorized users cannot access account
- User can manually log out

---

# Order Taxi

## US-05 Quick Driver Search

### User Story
As a customer,  
I want quick driver search,  
so that I can reach my destination faster.

### Acceptance Criteria
- Customer can enter pickup location
- System searches nearby drivers
- Available drivers are displayed
- Driver receives ride request
- Customer sees estimated arrival time

---

## US-06 Nearby Orders for Drivers

### User Story
As a driver,  
I want to receive nearby ride requests,  
so that I can get more orders efficiently.

### Acceptance Criteria
- Driver receives nearby ride requests
- System sorts rides by distance
- Driver can accept or reject request
- Accepted ride becomes unavailable for others
- Driver receives customer information

---

## US-07 Automatic Price Calculation

### User Story
As a customer,  
I want the system to calculate ride price automatically,  
so that I can estimate trip cost before ordering.

### Acceptance Criteria
- System calculates ride price automatically
- Price depends on trip distance
- Additional fees are included
- Customer sees estimated total price
- Price updates after route changes

---

## US-08 Driver Rating Visibility

### User Story
As a customer,  
I want to see driver ratings,  
so that I can choose a comfortable and trusted driver.

### Acceptance Criteria
- Customer can view driver rating
- Rating is displayed correctly
- Rating contains average score
- Customer can see reviews
- Only completed rides affect rating

---

# Ride Cancellation

## US-09 Cancel Ride

### User Story
As a customer,  
I want to cancel a ride quickly,  
so that I do not waste time if plans change.

### Acceptance Criteria
- Customer can cancel ride before pickup
- System updates ride status
- Driver receives cancellation notification
- Customer receives confirmation message
- Cancelled ride is saved in history

---

# Driver Rating

## US-10 Rate Driver

### User Story
As a customer,  
I want to rate the driver after the trip,  
so that other users can see service quality.

### Acceptance Criteria
- Customer can rate driver after trip
- Rating scale is from 1 to 5
- Customer can leave comment
- System saves rating
- Driver rating updates automatically

---

## US-11 Driver Receives Ratings

### User Story
As a driver,  
I want customers to rate me after rides,  
so that I can maintain a good reputation.

### Acceptance Criteria
- Driver receives customer ratings
- Ratings affect overall score
- Driver can see feedback history
- System calculates average rating
- Only completed trips can be rated