# Challenge 1 – Library Book Checkout System

## Challenge Overview

Build a comprehensive library management system that enables multiple user roles to manage book inventory and lending operations. The system should handle user registration, book cataloging, real-time availability tracking, and checkout/return workflows.

### Key Requirements

- **Admin functionality** for managing users and book inventory
- **User functionality** for discovering and checking out books
- **Real-time tracking** of book availability and checkout history
- **Business logic** to enforce lending rules and prevent conflicts
- **Persistent storage** for all data

---

## Problem Domain Breakdown

### 1. User Management
- Support different user roles (Admin, Librarian, Member)
- User registration and profile management
- Track user checkout history and outstanding items

### 2. Book Catalog
- Maintain a comprehensive book database with metadata (title, author, ISBN, etc.)
- Support multiple copies of the same book with unique identifiers
- Enable filtering and search by title, author, category, or ISBN

### 3. Checkout/Return Operations
- Implement checkout workflow with availability checks
- Manage return operations with late fee calculation
- Prevent double-checkout and handle edge cases

### 4. Data Persistence
- Store user, book, and transaction data persistently
- Maintain transaction history for audit and reporting
- Ensure data integrity across concurrent operations

### 5. Business Rules
- Enforce maximum books per user limit
- Calculate and track overdue items (books out >14 days)
- Generate reports on inventory status and member activity

---

## Core Entities & Relationships

```
User (id, name, email, role, joinDate)
  ├── Member (maxBooks: 5, currentBooks: [])
  └── Admin/Librarian (permissions)

Book (id, title, author, isbn, category, copies[])
  └── BookCopy (copyId, status, checkedOutBy, checkedOutDate, dueDate)

Checkout (id, userId, bookCopyId, checkoutDate, dueDate, returnDate)
```

---

## Core Features to Implement

### 1. User Management API
- User registration and authentication
- Role-based access control (Admin, Member)
- User profile and checkout history endpoints

### 2. Book Management API
- Add/update/delete books from catalog
- Track multiple copies per book
- Search and filter (title, author, category, ISBN, availability)

### 3. Checkout Operations API
- **Checkout**: Check availability → Reserve → Update status
- **Return**: Validate return → Calculate late fees → Update status
- **List**: Available books, user's checked-out books, overdue items

### 4. Reporting & Analytics
- Inventory status reports
- Member activity reports
- Overdue notifications
- Popular books statistics

---

## Tech Stack Options

Choose your preferred technology combination:

### Option 1: Python
**Backend**: Django/FastAPI | **Database**: SQLite/PostgreSQL | **Testing**: pytest | **Frontend**: React/Vue/Flask templates

### Option 2: Java
**Backend**: Spring Boot | **Database**: H2/PostgreSQL | **Testing**: JUnit5 + Mockito | **Frontend**: React/Thymeleaf

### Option 3: Node.js
**Backend**: Express/NestJS | **Database**: MongoDB/PostgreSQL | **Testing**: Jest | **Frontend**: React/Vue/EJS

### Option 4: Other
Use any language/framework of your choice - focus on the functionality, not the stack.

---

## Development Workflow Phases

Follow these phases in order for successful completion:

1. **Requirement Document** - Define functional and non-functional requirements for the library system
2. **Plan** - Design database schema, API architecture, and component interactions
3. **Instructions** - Write implementation guide for your chosen tech stack
4. **Prompts** - Define prompts to assist with code generation
5. **Chat Participants and Variables** - Set up collaboration context and variables
6. **Agents** - Configure any custom agents for your domain
7. **Custom Agent** - Create specialized agent for library-specific business logic
8. **Generating Code Using Agent/Custom Agent** - Generate project scaffold and initial code
9. **API Generation** - Implement REST endpoints for all entities and operations
10. **UI Generation** - Build user interfaces for member and admin workflows
11. **Unit Test Cases** - Write unit tests for business logic and edge cases
12. **Automation Testing** - Implement integration and end-to-end tests
13. **Documentation** - Create API docs, user guides, and technical documentation

---

## Expected Deliverables

- ✅ **Source Code** in `/src` folder (organized by layers: model, service, controller, util)
- ✅ **Test Suite** with unit and integration tests (min 70% coverage)
- ✅ **API Documentation** in `/docs/API.md` (endpoints, request/response schemas)
- ✅ **User Guide** in `/docs/USER_GUIDE.md` (workflows, features)
- ✅ **Technical Documentation** in `/docs/TECHNICAL.md` (architecture, database schema)
- ✅ **Database Schema** in `/docs/DATABASE_SCHEMA.md`
- ✅ **Sample Data** in `/data/sample.json` or equivalent

---

## Validation Criteria

Your solution will be validated against:

- ✅ **App Must Be Running** - Application starts without errors, all endpoints accessible
- ✅ **Tests Must Be Passing** - 100% of unit and integration tests pass with >70% code coverage
- ✅ **Exceptions/Errors Must Be Handled** - Graceful error handling with meaningful messages for invalid operations
- ✅ **Documents Must Be Present in /docs Folder** - Complete API docs, user guide, and technical documentation
- ✅ **Source Code Must Be Present in /src Folder** - Well-organized, readable code with proper structure

---

## Challenge Extension Ideas (If Time Permits)

- Implement reservation system for unavailable books
- Add email notifications for due dates and availability
- Create admin dashboard with analytics
- Implement fine/penalty system with payment tracking
- Add book recommendations based on checkout history
- Support book requests and waitlist functionality

---

**END OF CHALLENGE 1**
