# Metro Ticket Booking System 🚇

[![ServiceNow](https://img.shields.io/badge/ServiceNow-Developer-green.svg)](https://developer.servicenow.com)
[![Version](https://img.shields.io/badge/v1.0.0-stable-blue.svg)]()
[![Status](https://img.shields.io/badge/Status-Completed-brightgreen.svg)]()

> A robust **ServiceNow-based Metro Ticket Management System** designed to automate complex fare calculations and streamline the user booking experience through a modern Service Portal interface.

---

## 🎯 Project Vision
Manual fare calculation and station tracking are prone to errors and administrative overhead. This system replaces manual processes with a **data-driven fare matrix**, ensuring accuracy, scalability, and an intuitive user interface for end-to-end metro operations.

## ⚙️ Core Architecture
| Component | Technology | Purpose |
| :--- | :--- | :--- |
| **Backend** | ServiceNow Tables | Data storage & normalization |
| **Logic** | Business Rules | Real-time fare calculation engine |
| **UI** | Service Portal | User-friendly booking portal |
| **Data Validation** | Client Scripts | Real-time input error handling |

[Image of ServiceNow relational database schema architecture]

---

## 🚀 Key Technical Highlights

### 1. Dynamic Fare Engine
Instead of hardcoding prices, I built a **Fare Matrix Table**. When a booking is submitted, a `Before` Business Rule dynamically:
* Calculates the absolute distance (in stops) between the `Starting Point` and `Ending Point`.
* Queries the Fare Matrix to match the distance bracket.
* Multiplies the base rate by the ticket quantity.

### 2. Intelligent Reference Handling
To solve the common ServiceNow `sys_id` display issue, I implemented:
* **Display Value Overrides:** Forced the system to show `Station Name` instead of the unique system identifier across all reference fields.
* **Ref List Layout Optimization:** Configured the reference picker popups for clean, at-a-glance navigation.

### 3. User Experience (UX)
* **Custom Service Portal Page:** Created a mobile-responsive form using the Catalog Item widget.
* **Input Validation:** Added `onChange` client scripts to prevent logical errors (e.g., selecting the same station for the start and end).

---

## 🛠 Setup & Configuration
1. **PDI Preparation:** Ensure your ServiceNow Personal Developer Instance (PDI) is running.
2. **Schema Import:** Initialize the three core tables: `Station Details`, `Fare Matrix`, and `Ticket Transactions`.
3. **Business Rule Activation:** Ensure the `Calculate Metro Fare` rule is set to `Active` and scoped correctly.
4. **Portal Configuration:** Drag the **Catalog Item** widget into your Service Portal Designer and point it to the `Metro Ticket Purchase` item.

---

## 📈 Learnings
* **Debugging at Scale:** Mastered the use of `gs.info` logs for real-time Business Rule tracking.
* **UI/UX Lifecycle:** Learned how to bridge the gap between "Backend Data" and "Front-facing Portals" using Widgets.
* **Data Normalization:** Learned the importance of `Sequence Numbers` in relational databases to enable mathematical operations.

---
*Developed by Nithish Kanna | Built for the ServiceNow Developer Community*
