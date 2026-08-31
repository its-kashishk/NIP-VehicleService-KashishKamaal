# 🚗 NIP-VehicleService-KashishKamaal

## Vehicle Service Management System

**Pega National Internship Program 2026**

A Pega-based Vehicle Service Management application designed to manage vehicle service requests through a structured case lifecycle—from request creation and inspection to approval and service execution.

The application demonstrates case management, data modeling, business rules, SLA configuration, automated routing, user interaction, and end-to-end service request processing using Pega.

> **Project principle:** The application provides a structured workflow for managing vehicle service requests while ensuring that each request progresses through defined stages with appropriate business rules, routing, and approval controls.

---

## 📑 Table of Contents

- [Project Overview](#project-overview)
- [Demo](#demo)
- [Problem Statement](#problem-statement)
- [Objectives](#objectives)
- [Key Features](#key-features)
  - [Vehicle Service Request](#vehicle-service-request)
  - [Case Lifecycle](#case-lifecycle)
  - [Vehicle Data Object](#vehicle-data-object)
  - [Total Cost Calculation](#total-cost-calculation)
  - [SLA Management](#sla-management)
  - [Automated Work Queue Routing](#automated-work-queue-routing)
  - [Approval Workflow](#approval-workflow)
- [Solution Architecture](#solution-architecture)
- [End-to-End Workflow](#end-to-end-workflow)
- [Case Lifecycle](#case-lifecycle-1)
- [Data Model](#data-model)
- [Business Rules](#business-rules)
- [SLA Configuration](#sla-configuration)
- [Work Queue Routing](#work-queue-routing)
- [User Stories](#user-stories)
- [Application Interface](#application-interface)
- [Testing and Validation](#testing-and-validation)
- [Pega Implementation](#pega-implementation)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Installation / Access](#installation--access)
- [How to Use](#how-to-use)
- [Project Deliverables](#project-deliverables)
- [Individual Contribution](#individual-contribution)
- [Project Status](#project-status)
- [Author](#author)
- [Disclaimer](#disclaimer)

---

## 📌 Project Overview

Vehicle servicing involves multiple activities such as collecting vehicle details, inspecting the vehicle, estimating service costs, obtaining approval, and carrying out the required service.

Without a structured workflow, service requests can become difficult to track and may lead to delays, incorrect routing, or incomplete processing.

The **Vehicle Service Management System** addresses this problem using Pega's case management capabilities.

The application models every service request as a **Vehicle Service Request case** and manages it through defined stages:

```text
Vehicle Service Request
          ↓
    Initial Stage
          ↓
      Inspection
          ↓
       Approval
          ↓
  Service Execution
          ↓
      Completion
```

The system also incorporates:

- Vehicle data management
- Calculated service cost
- SLA management
- Vehicle-type-based routing
- Approval processing
- Structured case progression
- Validation through test scenarios

---

## 🎥 Demo

A demonstration of the completed application can be provided through the project submission/demo evidence.

> Screenshots and demonstration evidence for the implemented user stories are included as part of the project documentation.

---

# 🎯 Problem Statement

Vehicle service centers need an organized mechanism to manage service requests from creation through completion.

A service request may involve:

- Customer and vehicle information
- Vehicle inspection
- Labor estimation
- Parts estimation
- Total service cost
- Approval
- Assignment to an appropriate work queue
- Service execution
- Completion of the request

Managing these activities manually can make it difficult to maintain visibility into the current status of a service request.

The objective of this project is to build a **Pega-based case management solution** that provides a structured and traceable workflow for vehicle service requests.

---

# 🎯 Objectives

The application aims to:

- Create and manage Vehicle Service Request cases.
- Capture relevant vehicle information.
- Organize service requests through defined lifecycle stages.
- Perform vehicle inspection as part of the workflow.
- Calculate total service cost automatically.
- Obtain approval before service execution.
- Route cases according to vehicle type.
- Apply SLA targets to service requests.
- Provide a clear user interface for case processing.
- Validate the application through defined user stories and test scenarios.
- Demonstrate an end-to-end working Pega application.

---

# ✨ Key Features

## 🚘 Vehicle Service Request

The primary case type of the application is:

**Vehicle Service Request**

The case captures the information required to process a vehicle service request and provides the workflow through which the request progresses.

---

## 🔄 Case Lifecycle

The case follows a structured lifecycle consisting of:

1. **Initial Stage**
2. **Inspection**
3. **Approval**
4. **Service Execution**

Each stage represents a specific part of the service management process.

```text
┌─────────────────────┐
│   Vehicle Service   │
│      Request        │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│   Initial Stage     │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│     Inspection      │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│      Approval       │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│  Service Execution  │
└──────────┬──────────┘
           ↓
      Completed
```

---

## 🚗 Vehicle Data Object

A dedicated **Vehicle** data object is used to represent vehicle-related information.

The data structure supports the service request workflow by keeping vehicle information organized and reusable.

The Vehicle data object is integrated into the Vehicle Service Request case.

---

## 💰 Total Cost Calculation

The application automatically calculates the total service cost using:

```text
Total Cost = Labor Cost + Parts Cost
```

This ensures that the total estimated service cost is derived consistently from the individual cost components.

### Example

```text
Labor Cost = ₹2,000
Parts Cost = ₹3,500

Total Cost = ₹5,500
```

The calculated value is used as part of the service approval process.

---

## ⏱️ SLA Management

The Vehicle Service Request case is configured with service-level targets:

| SLA Component | Target |
|---|---:|
| Goal | 2 days |
| Deadline | 3 days |

The SLA configuration helps track whether service requests are progressing within the expected timeframe.

```text
Case Created
     │
     ├──────────── Goal: 2 Days
     │
     └──────────────── Deadline: 3 Days
```

---

## 🔀 Automated Work Queue Routing

The application includes routing logic based on **Vehicle Type**.

The purpose of this rule is to direct service requests to the appropriate work queue based on the vehicle category selected in the request.

```text
Vehicle Type
     ↓
Routing Decision
     ↓
Appropriate Work Queue
     ↓
Service Processing
```

This reduces manual assignment and helps ensure that requests reach the appropriate processing queue.

---

## ✅ Approval Workflow

Before the request proceeds to service execution, the service request passes through the **Approval** stage.

The approval step provides a controlled point at which the proposed service work and associated cost can be reviewed before execution.

```text
Inspection
    ↓
Service Cost
    ↓
Approval
   / \
  /   \
Approved  Not Approved
  ↓
Service Execution
```

---

# 🏗️ Solution Architecture

The application follows a case-driven architecture using Pega's workflow and business-rule capabilities.

```text
                 User
                  │
                  ▼
        Vehicle Service Request
                  │
                  ▼
           Initial Stage
                  │
                  ▼
             Inspection
                  │
          ┌───────┴───────┐
          │               │
          ▼               ▼
     Vehicle Data    Cost Calculation
          │               │
          └───────┬───────┘
                  ▼
              Approval
                  │
                  ▼
        Vehicle-Type Routing
                  │
                  ▼
         Service Execution
                  │
                  ▼
             Completion
```

### Main logical components

| Component | Purpose |
|---|---|
| Case Type | Vehicle Service Request |
| Data Object | Vehicle |
| Stages | Initial, Inspection, Approval, Service Execution |
| Calculation | Labor Cost + Parts Cost |
| SLA | 2-day goal / 3-day deadline |
| Routing | Vehicle Type-based work queue |
| Approval | Controls transition to service execution |

---

# 🔄 End-to-End Workflow

The complete workflow is:

```text
1. Create Vehicle Service Request
              ↓
2. Enter Vehicle Information
              ↓
3. Submit Request
              ↓
4. Initial Stage
              ↓
5. Vehicle Inspection
              ↓
6. Enter Labor and Parts Cost
              ↓
7. Calculate Total Cost
              ↓
8. Approval
              ↓
9. Route According to Vehicle Type
              ↓
10. Service Execution
              ↓
11. Complete Service Request
```

The workflow ensures that each request follows a consistent processing sequence.

---

# 📋 Case Lifecycle

## Stage 1 — Initial Stage

The service request is created and the required initial information is captured.

Typical information includes:

- Vehicle information
- Service request details
- Vehicle type
- Relevant customer/request information

---

## Stage 2 — Inspection

The vehicle is inspected and the service requirements are identified.

The inspection stage supports the determination of the work and cost required for the service.

---

## Stage 3 — Approval

The estimated service cost and request details are reviewed.

The case proceeds based on the configured approval workflow.

---

## Stage 4 — Service Execution

Once approved, the request proceeds to service execution.

The service team can process the requested work and move the case toward completion.

---

# 🗂️ Data Model

The application uses a **Vehicle** data object to represent vehicle information.

Conceptually:

```text
Vehicle
│
├── Vehicle Type
├── Vehicle Information
└── Service-related Information
```

The Vehicle information is consumed by the Vehicle Service Request case.

The application also uses service-cost information for the calculated total:

```text
Labor Cost
     +
Parts Cost
     ↓
Total Cost
```

---

# ⚙️ Business Rules

The application demonstrates multiple Pega business rules.

### 1. Total Cost Calculation

```text
Total Cost = Labor Cost + Parts Cost
```

### 2. Vehicle-Type-Based Routing

The selected vehicle type determines the appropriate work queue for processing.

### 3. Approval Control

The request must pass through the Approval stage before service execution.

### 4. SLA Management

The case is governed by the configured:

- Goal: 2 days
- Deadline: 3 days

---

# ⏱️ SLA Configuration

The configured SLA is:

| Parameter | Value |
|---|---|
| Goal | 2 days |
| Deadline | 3 days |

The SLA provides measurable service expectations for the case.

The configuration is intended to help identify requests that require attention before the deadline is exceeded.

---

# 🔀 Work Queue Routing

Routing is based on the **Vehicle Type** selected in the service request.

The routing logic follows the concept:

```text
              Vehicle Type
                   │
          ┌────────┼────────┐
          ↓        ↓        ↓
       Type A    Type B    Type C
          │        │        │
          ↓        ↓        ↓
      Work Queue Work Queue Work Queue
```

The actual configured vehicle types and queues are represented in the Pega application.

---

# 🧪 User Stories

The application was implemented and validated against the required user stories **US-001 through US-010**.

| User Story | Area | Evidence |
|---|---|---|
| US-001 | Vehicle Service Request creation | Screenshot |
| US-002 | Vehicle information / data capture | Screenshot |
| US-003 | Initial case processing | Screenshot |
| US-004 | Inspection stage | Screenshot |
| US-005 | Service cost calculation | Screenshot |
| US-006 | Approval workflow | Screenshot |
| US-007 | SLA configuration / processing | Screenshot |
| US-008 | Vehicle-type-based routing | Screenshot |
| US-009 | Service execution | Screenshot |
| US-010 | End-to-end case completion | Screenshot |

> Each required user story is supported by its corresponding application screenshot in the project evidence.

---

# 🖥️ Application Interface

The application provides a Pega case-management interface for creating and processing Vehicle Service Requests.

The main interface supports:

- Case creation
- Vehicle information entry
- Service request details
- Inspection processing
- Cost information
- Approval
- Service execution
- Case progression

### Application Evidence

Screenshots demonstrating the completed application can be added to the repository using the following structure:

```text
screenshots/
├── US-001.png
├── US-002.png
├── US-003.png
├── US-004.png
├── US-005.png
├── US-006.png
├── US-007.png
├── US-008.png
├── US-009.png
└── US-010.png
```

---

# 🧪 Testing and Validation

Testing was performed by processing Vehicle Service Request cases through the implemented workflow and verifying the configured business behavior.

### Functional areas validated

- Case creation
- Vehicle data capture
- Case stage progression
- Inspection processing
- Cost calculation
- Approval
- SLA configuration
- Vehicle-type routing
- Service execution
- Case completion

### Calculation Validation

The total cost calculation was verified using:

```text
Total Cost = Labor Cost + Parts Cost
```

### Workflow Validation

The case was verified across the lifecycle:

```text
Initial
  ↓
Inspection
  ↓
Approval
  ↓
Service Execution
```

### Routing Validation

Vehicle-type-based routing was checked to confirm that the case is directed to the configured work queue.

---

# 🛠️ Pega Implementation

The project uses Pega's low-code application development and case-management capabilities.

The implementation includes:

- Application configuration
- Case type configuration
- Case lifecycle stages
- Views and forms
- Data objects
- Fields and properties
- Calculated properties
- Business rules
- Approval workflow
- SLA configuration
- Work queue routing
- Case processing

The application was developed in the Pega exercise environment as part of the **Pega National Internship Program**.

---

# 💻 Technology Stack

| Technology | Purpose |
|---|---|
| Pega Platform | Application development |
| Pega Case Management | Service request lifecycle |
| Pega Data Objects | Vehicle data management |
| Pega Business Rules | Application logic |
| Pega SLA | Service-level management |
| Pega Work Queues | Case routing |
| Pega UI | User interaction and case processing |

---

# 📁 Project Structure

A recommended repository structure is:

```text
NIP-VehicleService-KashishKamaal/
│
├── README.md
│
├── screenshots/
│   ├── US-001.png
│   ├── US-002.png
│   ├── US-003.png
│   ├── US-004.png
│   ├── US-005.png
│   ├── US-006.png
│   ├── US-007.png
│   ├── US-008.png
│   ├── US-009.png
│   └── US-010.png
│
├── documentation/
│   └── Project-Summary.pdf
│
└── submission/
    └── required-project-files
```

The exact structure may vary depending on the files required for the final internship submission.

---

# 🚀 Installation / Access

This project is implemented on the **Pega Platform** and is intended to be accessed through the configured Pega environment.

The application does not require a traditional local Python installation.

To use the application:

1. Access the assigned Pega environment.
2. Sign in using the registered credentials.
3. Open the Vehicle Service Management application.
4. Create a Vehicle Service Request.
5. Process the case through its lifecycle.
6. Verify the configured business rules and workflow behavior.

---

# 📖 How to Use

## 1. Create a Service Request

Create a new **Vehicle Service Request** case.

Enter the required vehicle and service information.

---

## 2. Process the Initial Stage

Review the submitted request and continue the case to the Inspection stage.

---

## 3. Perform Inspection

Process the vehicle inspection and capture the required service information.

---

## 4. Enter Service Costs

Provide:

- Labor Cost
- Parts Cost

The application calculates:

```text
Total Cost = Labor Cost + Parts Cost
```

---

## 5. Approve the Request

Review the service request and estimated cost through the Approval stage.

---

## 6. Route the Case

The application applies vehicle-type-based routing to determine the appropriate work queue.

---

## 7. Execute the Service

The approved service request proceeds to Service Execution.

---

## 8. Complete the Case

After the service has been processed, complete the Vehicle Service Request case.

---

# 📦 Project Deliverables

The project deliverables include the implemented Pega application and supporting submission evidence.

### Application Deliverables

- Vehicle Service Management application
- Vehicle Service Request case type
- Vehicle data object
- Configured case lifecycle
- Total Cost calculation
- SLA configuration
- Vehicle-type-based routing
- Approval workflow
- Service Execution workflow

### Evidence Deliverables

- US-001 to US-010 screenshots
- Application demonstration
- Test evidence
- Project documentation
- Individual Project Summary
- Required internship submission files

---

# 👩🏻‍💻 Individual Contribution

This is an individual project.

The implementation contribution covers the end-to-end development of the Vehicle Service Management application, including:

- Understanding the internship requirements.
- Translating the requirements into a Pega case-management workflow.
- Creating the Vehicle Service Request case type.
- Configuring the case lifecycle.
- Creating and configuring the Vehicle data object.
- Configuring application fields and views.
- Implementing Total Cost calculation.
- Configuring the 2-day Goal and 3-day Deadline SLA.
- Implementing vehicle-type-based work queue routing.
- Configuring the Approval stage.
- Configuring Service Execution.
- Testing the complete case lifecycle.
- Validating the required user stories.
- Capturing application screenshots.
- Preparing project documentation and submission evidence.

---

# 📊 Project Status

## Completed

- [x] Pega application created
- [x] Vehicle Service Request case type configured
- [x] Initial Stage configured
- [x] Inspection stage configured
- [x] Approval stage configured
- [x] Service Execution stage configured
- [x] Vehicle data object configured
- [x] Vehicle information captured
- [x] Total Cost calculation implemented
- [x] SLA configured
- [x] Vehicle-type-based routing configured
- [x] Approval workflow implemented
- [x] End-to-end case workflow tested
- [x] Required user-story evidence captured
- [x] Project documentation prepared

## Final Submission

- [x] Application implementation
- [x] Screenshots
- [x] Project documentation
- [x] Submission evidence

---

# 👤 Author

**Kashish Kamaal**

**Pega National Internship Program 2026**

Project: **Vehicle Service Management System**

Application: **NIP-VehicleService-KashishKamaal**

College: **LNCT Group of Colleges**

---

# ⚠️ Disclaimer

This project is an educational application developed as part of the **Pega National Internship Program 2026**.

The Vehicle Service Management System demonstrates case management, workflow automation, business rules, SLA management, routing, and data handling using the Pega Platform.

The application is intended for educational and demonstration purposes and should not be interpreted as a production vehicle-service platform without appropriate security, validation, integration, and operational controls.