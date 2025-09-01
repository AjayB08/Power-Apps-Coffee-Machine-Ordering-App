# ☕ Coffee Machine Ordering Solution – Microsoft Power Platform

## 📌 Overview
This project demonstrates how **Canvas Apps**, **Model-Driven Apps**, **Dataverse**, and **Power Automate Flows** can work together to automate an ordering process.

The solution allows employees to **browse, compare, and order coffee machines** through a **Canvas App**.  
It then manages the **approval workflow** using **Power Automate** and tracks the **order lifecycle** in a **Model-Driven App** with a **Business Process Flow**.

---

## 🚀 Features

### **1. Canvas App – Coffee Machine Ordering**
- Reads available coffee machines from **Excel**.
- Allows:
  - Searching and filtering coffee machines.
  - Comparing multiple machines.
  - Placing an order.
- Saves orders to **Dataverse**.

### **2. Model-Driven App – Order Lifecycle Management**
- Built on **Dataverse** to manage coffee machine orders.
- Implements a **Business Process Flow (BPF)**:
  1. Order Placement
  2. Approval Stage (for higher-value machines)
  3. Fulfillment
  4. Customer Feedback (Survey)

### **3. Automated Approval Workflow (Power Automate)**
- Triggered when a new order is placed in the Canvas App.
- Sends approval requests to:
  - **Microsoft Outlook**
  - **Microsoft Teams**
  - **Power Automate Approvals**
- Sends confirmation email to requester.

---

## 🛠️ Tech Stack
| Component | Technology |
|-----------|------------|
| **Frontend** | Power Apps Canvas App |
| **Backend** | Microsoft Dataverse |
| **Automation** | Power Automate |
| **Order Management** | Model-Driven App |
| **Data Source** | Excel |
| **Approvals** | Outlook, Teams, Power Automate |

---


---

## 📸 Screenshots
1. **Canvas App – Coffee Machine Selection**
<img width="1356" height="637" alt="Coffee_Machine_Ordering_App_Home" src="https://github.com/user-attachments/assets/557d6fee-7f45-458a-b879-6a9e07a72ad1" />
<img width="1347" height="576" alt="Coffee_Machine_Ordering_App_Compare" src="https://github.com/user-attachments/assets/064d1b54-2dc1-43f1-9405-7f1256085f00" />
<img width="1359" height="636" alt="Coffee_Machine_Ordering_App_Submit" src="https://github.com/user-attachments/assets/7e062d59-bece-4675-a4c2-47cdede5ca56" />

3. **Model-Driven App – Order Lifecycle**
   <img width="1339" height="503" alt="Coffee_Machine_Order_Model_Driven_App" src="https://github.com/user-attachments/assets/7ab07ac6-022c-4384-a723-f96ebf1a78b8" />

5. **Power Automate – Approval Email**
6. **Survey Form – Feedback Collection**
<img width="1347" height="586" alt="Coffee_Machine_Order_Model_Driven_App_Page2" src="https://github.com/user-attachments/assets/6b4bcf81-ae58-48d2-9685-9997d7e8f43f" />

---

## 📊 Business Process Flow Stages
| Stage | Description |
|-------|-------------|
| **Order Placement** | Triggered when the Canvas App user submits an order. |
| **Approval** | Required for higher-priced machines. Approvers get notified via multiple channels. |
| **Fulfillment** | Order is processed once approved. |
| **Survey** | Customer receives a survey form after order fulfillment. |

---

## 📧 Approval Flow Logic
1. **Trigger** – New order record in Dataverse.
2. **Condition** – Check if price exceeds threshold.
3. **Approval Request** – Sent to approvers via Outlook, Teams, Approvals Center.
4. **Outcome** – Approve/Reject decision captured.
5. **Notify Requestor** – Send confirmation email.

---

## 🎯 Use Cases
- Corporate IT departments ordering office equipment.
- Employee self-service portals for office supplies.
- Automating procurement requests with approval workflows.

---

## 📂 Solution Architecture

### **Mermaid Diagram**

```mermaid
flowchart TD
    A[Excel - Machine Data] --> B[Canvas App - Select & Order]
    B --> C[Dataverse - Order Storage]
    C --> D[Power Automate Flow - Approval Trigger]
    D --> E{Approval Needed?}
    E -- Yes --> F[Send Approval Request<br>Outlook / Teams / Approvals]
    E -- No --> H[Order Fulfillment]
    F --> G[Approve / Reject]
    G --> H[Order Fulfillment]
    H --> I[Survey Form - Customer Feedback]

