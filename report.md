# 📚 Library Management System — UML Design Report


## 👥 Contributors

| Name   | Responsibility |
|--------|----------------|
| Khondamir Tuychiev | UML Modeling & System Design |
| Boburjon Komilov   | Diagram Development |
| Abdulaziz Maxammadjonov | Analysis & Documentation |

---
## 📌 Project Overview

This project models a **Library Management System** using UML diagrams to describe system behavior, structure, and interaction flows before implementation.

The system supports multiple user roles and core library operations such as:

* User registration and login
* Book searching and reservation
* Book issuing and returning
* Catalog management
* Overdue tracking and fine handling

To design and analyze the system, the following UML diagrams were created:

* ✅ Use Case Diagram
* ✅ Class Diagram
* ✅ Sequence Diagram

These diagrams together provide a complete view of **what the system does**, **how it is structured**, and **how components interact over time**.

---

# (1) 🎭 Use Case Diagram

## Purpose

The Use Case Diagram describes the **functional behavior** of the system from the user’s perspective. It shows what actions each actor can perform and how they interact with the system.

---

## 👥 Actors

| Actor           | Description                                                       |
| --------------- | ----------------------------------------------------------------- |
| User (Customer) | Library member who searches, borrows, reserves, and returns books |
| Librarian       | Administrator who manages books and verifies members              |
| System          | Processes transactions and business logic                         |
| Database        | Stores book and member records                                    |

---

## 🎯 Main Use Cases

| Use Case       | Actor           | Description              |
| -------------- | --------------- | ------------------------ |
| Register       | User            | Create a new account     |
| Login          | User, Librarian | Authenticate into system |
| Search Book    | User, Librarian | Find books in catalog    |
| Issue Book     | User, Librarian | Borrow a book            |
| Reserve Book   | User, Librarian | Reserve unavailable book |
| Return Book    | User            | Return borrowed book     |
| Pay Fine       | User            | Pay overdue fine         |
| Add Book       | Librarian       | Add new book             |
| Update Book    | Librarian       | Modify book details      |
| Remove Book    | Librarian       | Delete book record       |
| Update Catalog | Librarian       | Maintain catalog         |
| Notify Overdue | System          | Send overdue alerts      |
| Calculate Fine | System          | Compute penalties        |

---

## 🔗 Use Case Relationships

| Relationship    | Description                                          |
| --------------- | ---------------------------------------------------- |
| **Include**     | `Return Book` includes `Pay Fine`                    |
| **Extend**      | `Add / Update / Remove Book` extend `Update Catalog` |
| **Association** | Actors connect to permitted actions                  |

---

# (2) 🧱 Class Diagram

## Purpose

The Class Diagram models the **static structure** of the system — classes, attributes, methods, and relationships.

---

## 🏷 Core Classes

### LibraryManagementSystem

| Type       | Members                                             |
| ---------- | --------------------------------------------------- |
| Attributes | id, name, username, password, phoneNum, email       |
| Methods    | createAccount(), login(), logout(), updateProfile() |

---

### Customer

| Type       | Members                                                                                   |
| ---------- | ----------------------------------------------------------------------------------------- |
| Attributes | username, password                                                                        |
| Methods    | login(), checkAccount(), searchBook(), issueBook(), returnBook(), reserveBook(), logout() |

---

### Librarian

| Type       | Members                                                                                                                 |
| ---------- | ----------------------------------------------------------------------------------------------------------------------- |
| Attributes | id, name                                                                                                                |
| Methods    | addBook(), searchBook(), updateBook(), issueBook(), removeBook(), returnBook(), reserveBook(), verifyMember(), logout() |

---

### Book

| Type       | Members                           |
| ---------- | --------------------------------- |
| Attributes | title, bookId, subject, author    |
| Methods    | displayBook(), updateBookStatus() |

---

### LibraryDatabase

| Type       | Members                                        |
| ---------- | ---------------------------------------------- |
| Attributes | list_of_books                                  |
| Methods    | add(), delete(), update(), search(), display() |

---

## 🔗 Class Relationships

| Relationship | Between              | Meaning                         |
| ------------ | -------------------- | ------------------------------- |
| Association  | Customer ↔ Book      | Customer borrows/searches books |
| Association  | Librarian ↔ Book     | Librarian manages books         |
| Association  | Librarian ↔ Database | Librarian updates records       |
| Association  | System ↔ Users       | System handles authentication   |

**Relationship Types Used:**

* Association
* Usage dependency
* System coordination

---
# 🔍 Comparison — Use Case Diagram vs Class Diagram

## Purpose Difference

| Aspect    | Use Case Diagram           | Class Diagram                |
| --------- | -------------------------- | ---------------------------- |
| Focus     | System functionality       | System structure             |
| Answers   | *What does the system do?* | *How is the system built?*   |
| Viewpoint | User perspective           | Developer/design perspective |
| Level     | High-level behavior        | Detailed static design       |

---

## When Each Diagram Is Used

**Use Case Diagram is used when:**

* Gathering requirements
* Understanding user interactions
* Defining system features
* Communicating with stakeholders
* Early design phase

**Class Diagram is used when:**

* Designing system architecture
* Planning implementation
* Defining data models
* Structuring code
* Pre-coding design phase

---

## Importance in System Design

**Use Case Diagram Importance:**

* Clarifies system goals
* Identifies actors and permissions
* Prevents missing features
* Aligns stakeholder expectations

**Class Diagram Importance:**

* Defines core entities
* Shows relationships between components
* Guides object-oriented implementation
* Reduces design errors before coding

---

## How They Complement Each Other

Use Case Diagrams define **what needs to be built**, while Class Diagrams define **how it will be built**.
Together they connect user requirements with technical structure, ensuring the final system design is both functional and implementable.

---

# (3) 🔄 Sequence Diagram

## Purpose

The Sequence Diagram shows **how components interact over time** to complete operations — especially the **book issuing process**.

---

## 🧩 Participants

* Customer
* Librarian
* Book
* System
* Database

---

## ▶️ Book Issue Interaction Flow

## Modeled Process: Book Issuing Transaction

| Step | Interaction                         |
| ---- | ----------------------------------- |
| 1    | Customer searches or requests book  |
| 2    | Librarian checks availability       |
| 3    | Book component returns status       |
| 4    | Customer requests issue             |
| 5    | Librarian checks issued-book limits |
| 6    | Librarian sends request to System   |
| 7    | System creates transaction          |
| 8    | System updates book status          |
| 9    | Database stores transaction         |
| 10   | Confirmation returned to Customer   |

---

## ⏱ Additional Flows Modeled

* Book return and renewal
* Overdue notification
* Fine calculation
* Adding new arrivals
* Updating/removing books

---

# 🧠 Actors, Use Cases, and Component Relationships

## Actors

Actors represent **external roles** interacting with the system. Each actor has clearly separated responsibilities:

* Users → borrowing operations
* Librarians → administrative control
* System → processing logic
* Database → persistent storage

---

## Use Cases

Use cases define **functional capabilities** such as issuing, reserving, and catalog maintenance.

They ensure:

* Clear feature boundaries
* Role-based permissions
* Functional completeness

---

## Relationships Between Components

| Type        | Example                            |
| ----------- | ---------------------------------- |
| Association | User interacts with Book           |
| Include     | Return Book → Pay Fine             |
| Extend      | Update Catalog ← Add/Update/Remove |
| Dependency  | System → Database                  |

---

# ✅ Why UML Modeling Was Useful

Using UML before coding provided several advantages:

* Clarified system requirements
* Identified actor responsibilities
* Defined class structure early
* Visualized interaction flows
* Reduced ambiguity in design
* Improved communication between team members

---

# 📦 Diagrams Included

This repository contains:

* 📌 Use Case Diagram — system functionality view
* 🧱 Class Diagram — structural design view
* 🔄 Sequence Diagram — interaction flow view

---


# 🏁 Conclusion

The Library Management System was successfully modeled using three UML diagram types. Each diagram contributed a different perspective:

| Diagram  | Focus                            |
| -------- | -------------------------------- |
| Use Case | What the system does             |
| Class    | How the system is structured     |
| Sequence | How the system behaves over time |

Together, they form a complete and well-defined system design that can guide implementation and team communication.

