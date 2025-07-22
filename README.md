# AceDeliveryApp
Delivery Management Web Application For Admin and Mini Program For Users

# 🍔 AceDeliveryApp

**AceDeliveryApp** 
It offers a WeChat Mini‑Program frontend for customers and a Spring Boot–powered back‑office for merchants, delivering an end‑to‑end workflow: menu browsing, ordering, real‑time updates, analytics, and order management.


---

## Project Overview

AceDeliveryApp recreates a real‑world takeaway workflow:

| Module            | Description                                                                                         |
| ----------------- | --------------------------------------------------------------------------------------------------- |
| **Mini‑Program**  | Customers browse menus, add to cart, place orders, pay, and receive order status in real time.      |
| **Merchant Portal** | Staff manage dishes, categories, orders, and see dashboard analytics.                              |
| **Data Center**   | Sales charts, order completion rate, effective orders, and other KPIs via ECharts visualizations.   |
| **Realtime**      | WebSocket pushes order reminders (催单) and live status updates.                                      |

---

## Feature Highlights

- **WeChat Mini‑Program** for seamless mobile ordering  
- **WeChat One‑Tap Login**  
- **Order Workflow** (cart → submit → pay → track)  
- **Real‑Time Reminders & Voice Alerts** via WebSocket  
- **Sales Dashboards** with ECharts (daily/weekly/monthly reports)  
- **Admin CRUD** for dishes, categories, and staff accounts  
- **Aliyun OSS** image storage for dish photos  

---

## Technology Stack

| Layer               | Technologies                                                                 |
| ------------------- | ----------------------------------------------------------------------------- |
| **Backend**         | Spring Boot, Spring MVC, Spring Cache, Spring Task                          |
| **Persistence**     | MyBatis + MySQL                                                               |
| **Cache / Message** | Redis                                                                         |
| **Real‑Time**       | Spring WebSocket                                                              |
| **Frontend (Admin)**| Vue2 + Element UI                                                             |
| **Frontend (User)** | WeChat Mini‑Program (WXML / WXSS / JS)                                        |
| **Charts**          | ECharts                                                                       |
| **Cloud Storage**   | Aliyun OSS                                                                    |
| **Build Tool**      | Maven                                                                         |

---

## Getting Started

### Prerequisites
- **Java 8** or higher  
- **Maven 3.6+**  
- MySQL 5.7+  
- Redis (for caching & pub/sub)  
- IDE such as IntelliJ IDEA / Eclipse  

### Installation

```bash
# 1. Clone repository
git clone git@github.com:AceWang377/AceDeliveryApp.git
cd AceDeliveryApp

# 2. Build project
mvn clean install

