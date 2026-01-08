# Nir App

# Software Requirements Specification (SRS)

## 1. Introduction

### 1.1 Purpose

This document describes the **Software Requirements Specification (SRS)** for **NIR App**, an Android-based water can delivery application. The SRS is intended for stakeholders including product owners, developers, designers, testers, and future maintainers to clearly understand the system’s functionality, constraints, and requirements.

### 1.2 Scope

NIR App is a **B2C + B2B Android application** that connects **water can business owners** with **consumers**. The system supports:

* Dual-role login (Owner & Consumer)
* On-demand and subscription-based water can delivery
* Multiple payment options (Cash, Wallet, UPI)
* Real-time delivery tracking
* Route optimization for delivery owners

The initial release targets **Android only**.

### 1.3 Definitions & Acronyms

* **User / Consumer**: End customer ordering water cans
* **Owner**: Water can supplier / delivery business
* **Subscription**: Recurring water delivery plan
* **Wallet**: In-app balance for payments
* **UPI**: Unified Payments Interface (PhonePe, GPay, etc.)
* **TSP**: Traveling Salesman Problem (route optimization)

---

## 2. Overall Description

### 2.1 Product Perspective

NIR App is a **client–server mobile application** consisting of:

* Android Mobile App
* Backend APIs
* Database
* Third-party services (Maps, Payments, Notifications)

### 2.2 User Classes

#### 2.2.1 Consumer

* Register & login
* Book water cans
* Subscribe to monthly plans
* Track delivery vehicle
* Make payments
* View dashboard & billing

#### 2.2.2 Business Owner

* Register & login
* Manage consumers
* View active orders
* Track delivery route & vehicle
* Optimize delivery routes
* View earnings & subscriptions

### 2.3 Operating Environment

* Android OS (Android 8.0 and above)
* Backend hosted on cloud (AWS/GCP/Azure)
* Internet connectivity required

### 2.4 Design Constraints

* Android-only platform
* Secure payment compliance
* Location permissions required
* Real-time updates require background services

---

## 3. System Features & Functional Requirements

### 3.1 Authentication & Role Management

#### Description

Users can log in either as **Consumer** or **Owner**, and each role sees a different UI and features.

#### Functional Requirements

* FR-1: System shall allow user registration
* FR-2: System shall support role-based login
* FR-3: System shall redirect users to role-specific dashboards
* FR-4: System shall support logout and session expiration

---

### 3.2 Consumer – Water Can Booking

#### Description

Consumers can book water cans for immediate delivery or schedule delivery.

#### Functional Requirements

* FR-5: Consumer shall select quantity of water cans
* FR-6: Consumer shall select delivery address
* FR-7: Consumer shall place on-demand orders
* FR-8: Consumer shall view order status

---

### 3.3 Subscription Management

#### Description

Consumers can subscribe to monthly water delivery plans.

#### Functional Requirements

* FR-9: Consumer shall view available subscription plans
* FR-10: Consumer shall subscribe/unsubscribe to plans
* FR-11: System shall auto-generate orders based on subscription
* FR-12: System shall calculate monthly billing

---

### 3.4 Payment System

#### Description

Supports post-delivery, upfront, and monthly subscription payments.

#### Functional Requirements

* FR-13: System shall support Cash on Delivery
* FR-14: System shall support in-app wallet
* FR-15: System shall integrate UPI payments (PhonePe, GPay)
* FR-16: System shall generate payment receipts
* FR-17: System shall maintain transaction history

---

### 3.5 Delivery Tracking & Notifications

#### Description

Consumers can track delivery vehicle in real time.

#### Functional Requirements

* FR-18: System shall show live vehicle location on map
* FR-19: System shall send notification when vehicle is 2 minutes away
* FR-20: System shall update delivery status in real time

---

### 3.6 Consumer Dashboard

#### Description

Dashboard provides full order and billing overview.

#### Functional Requirements

* FR-21: Consumer shall view order history
* FR-22: Consumer shall view subscription details
* FR-23: Consumer shall view total monthly bill
* FR-24: Consumer shall download invoices

---

### 3.7 Owner – Order & Customer Management

#### Description

Owners manage customers, orders, and delivery operations.

#### Functional Requirements

* FR-25: Owner shall view subscribed consumers
* FR-26: Owner shall view consumer personal details
* FR-27: Owner shall view active orders
* FR-28: Owner shall view consumer locations on map

---

### 3.8 Route Optimization

#### Description

System calculates optimal delivery route visiting each customer once with minimal cost.

#### Functional Requirements

* FR-29: System shall calculate optimized delivery route
* FR-30: System shall display route on map
* FR-31: System shall support real-time route updates

#### Algorithm Requirement

* Use **TSP heuristic (Nearest Neighbor / Google Directions API optimization)**

---

## 4. Non-Functional Requirements

### 4.1 Performance

* App should load main screens within 2 seconds
* Location updates every 5–10 seconds

### 4.2 Security

* Secure authentication (JWT/OAuth)
* Encrypted payment transactions
* Role-based access control

### 4.3 Scalability

* Support multiple owners and thousands of users
* Horizontally scalable backend

### 4.4 Reliability

* 99% uptime
* Offline handling for poor connectivity

### 4.5 Usability

* Simple UI for non-technical users
* Local language support (future scope)

---

## 5. External Interface Requirements

### 5.1 User Interface

* Material Design (Android)
* Separate UI flows for Owner & Consumer

### 5.2 Hardware Interfaces

* GPS for location tracking

### 5.3 Software Interfaces

* Google Maps API
* Firebase Cloud Messaging (notifications)
* Payment Gateway SDKs

---

## 6. System Architecture (High-Level)

```
[ Android App ]
     |
[ REST API Layer ]
     |
[ Business Logic ]
     |
[ Database ]
```

---

## 7. Future Enhancements

* iOS version
* Multiple delivery vehicles
* Admin panel
* AI-based demand prediction
* Ratings & reviews
* Multiple products other then water can
* scaner system to added your store on users phone

---

## 8. Assumptions & Dependencies

* Internet availability
* Google Maps & Payment APIs availability
* Owner has delivery vehicle

---

## 9. Conclusion

This SRS defines a scalable, production-ready foundation for **NIR App**, enabling efficient water delivery operations with real-time tracking, optimized routing, and flexible payment options.

---

**Document Version:** 1.0
**Platform:** Android Only
