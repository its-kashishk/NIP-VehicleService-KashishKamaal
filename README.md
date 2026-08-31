# 🚗 Vehicle Service Management System

## NIP – Pega Platform Project

**Application Name:** NIP-VehicleService-KashishKamaal  
**Platform:** Pega Platform  
**Version:** Pega Infinity 25.1.3  
**Project:** National Internship Program (NIP) – Vehicle Service Management

---

## 📌 Project Overview

The Vehicle Service Management application is a Pega-based workflow application designed for UrbanFleet Operations to manage the complete vehicle servicing lifecycle.

The application allows customers to raise vehicle service requests, enables service advisors to inspect vehicles and prepare service estimates, allows customers to approve or reject estimates, automatically routes service work to technicians, tracks service-level agreements, and notifies customers when servicing is completed.

The application provides a structured workflow from service request creation to final completion.

---

## 🎯 Objectives

The main objectives of the application are:

- Allow customers to submit vehicle service requests.
- Capture and maintain vehicle information.
- Enable service advisors to inspect vehicles.
- Generate service estimates automatically.
- Allow customers to review and approve/reject estimates.
- Automatically assign service work to technicians.
- Route requests according to vehicle type.
- Track service SLAs.
- Notify customers after service completion.
- Provide an end-to-end digital service workflow.

---

## 🔄 Case Lifecycle

The main case type is:

### Vehicle Service Request

The case follows the following lifecycle:

1. **Request Intake**
   - Collect Service Data
   - Record Symptoms
   - Confirm Intake

2. **Inspection**
   - Assign Advisor
   - Inspect Vehicle
   - Estimate Generation
   - Notify Customer

3. **Customer Approval**
   - Estimate Review
   - Customer Decision
   - Update Status
   - Notify Outcome

4. **Service Execution**
   - Assign Technician
   - Service Vehicle
   - Track SLA
   - Notify Progress

5. **Completion**
   - Confirm Completion
   - Generate Report
   - Notify Customer

---

## 👥 Personas

The application includes the following personas:

- **Customer** – Raises service requests, reviews estimates and approves or rejects service estimates.
- **Service Advisor** – Inspects vehicles and prepares service estimates.
- **Technician** – Performs vehicle servicing and updates service status.
- **Fleet Manager** – Monitors fleet servicing, SLAs and vehicle uptime.
- **System Administrator** – Manages application configuration, users, roles and security.
- **Notification Recipient** – Receives service-related notifications.
- **Application Control Agent** – Provides autonomous application-level assistance and orchestration.

---

## 🗃️ Data Objects

The application contains reusable data objects for managing vehicle service information:

- Customer
- Vehicle
- Service Request
- Service Estimate
- Service Appointment
- Service Technician
- Service Notification

These data objects help maintain consistent information across different service requests and support vehicle service history.

---

## ⚙️ Key Features

### 1. Vehicle Service Request

Customers can create a service request by providing vehicle information and describing the service issue.

Important information includes:

- Vehicle ID
- Vehicle Model
- Issue Description
- Vehicle Type

Required information is validated before the request proceeds.

---

### 2. Vehicle Inspection

The Service Advisor performs an inspection and records:

- Inspection Notes
- Condition Rating
- Inspection Status

The inspection must be completed before the estimate process continues.

---

### 3. Service Estimate

The Service Advisor enters:

- Labor Cost
- Parts Cost

The application calculates:

```text
Total Cost = Labor Cost + Parts Cost
