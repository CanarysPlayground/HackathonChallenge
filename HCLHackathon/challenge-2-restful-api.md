# Challenge 2 – Build a Comprehensive E-Commerce Product Management API

## Challenge Overview

Design and build a robust REST API for an e-commerce platform that manages product inventory, catalogs, and operations. The API should support product discovery, filtering, CRUD operations, and maintain data consistency.

### Key Requirements

- **Product Catalog Management** - Create, read, update, delete product information
- **Advanced Filtering & Search** - Filter by category, price range, availability
- **Inventory Tracking** - Monitor stock levels and availability
- **Data Validation** - Ensure data integrity and prevent invalid operations
- **Error Handling** - Graceful error responses with meaningful messages
- **API Documentation** - Clear, well-documented endpoints

---

## Problem Domain Breakdown

### 1. Product Domain
- Product properties: ID, name, description, price, category, stock quantity, rating, tags
- Support for product categorization and hierarchies
- Manage product metadata and attributes

### 2. Inventory Management
- Track stock levels and availability status
- Prevent negative inventory
- Support stock updates and reservations
- Handle out-of-stock scenarios

### 3. Search & Filtering
- Filter by category (Electronics, Clothing, Books, etc.)
- Price range filtering (min/max)
- Availability filtering (in-stock/out-of-stock)
- Full-text search on product names and descriptions
- Sorting (by price, rating, name, date added)

### 4. CRUD Operations
- **Create** - Add new products with validation
- **Read** - Retrieve single product or all products with pagination
- **Update** - Modify product details atomically
- **Delete** - Remove products with proper cleanup

### 5. Data Persistence
- Reliable storage of product data
- Transaction support for atomic operations
- Audit trail for product changes
- Efficient querying and indexing

---

## Core Data Model

```
Product {
  id: unique identifier
  name: string (required, non-empty)
  description: text (optional)
  category: string (Electronics, Clothing, Books, etc.)
  price: decimal (required, >= 0)
  stock_quantity: integer (>= 0)
  rating: float (0-5, optional)
  tags: array (optional)
  created_at: timestamp
  updated_at: timestamp
}

Category {
  id: unique identifier
  name: string (required, unique)
  description: text
  parent_id: reference to parent category (optional)
}
```

---

## API Endpoints to Implement

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/products` | List all products with pagination |
| GET | `/api/products?category={cat}&minPrice={min}&maxPrice={max}` | Filter products |
| GET | `/api/products/{id}` | Get product by ID |
| POST | `/api/products` | Create new product |
| PUT | `/api/products/{id}` | Update product details |
| DELETE | `/api/products/{id}` | Delete product |
| GET | `/api/categories` | List all categories |
| POST | `/api/categories` | Create new category |
| GET | `/api/products/search?q={query}` | Search products by name/description |

### Query Parameters
- `page`: Page number (default: 1)
- `pageSize`: Items per page (default: 20, max: 100)
- `category`: Filter by category name
- `minPrice`: Minimum price filter
- `maxPrice`: Maximum price filter
- `sortBy`: Sort field (price, rating, name, date)
- `sortOrder`: asc or desc
- `inStock`: true/false filter

---

## Tech Stack Options

Choose your preferred technology combination:

### Option 1: Python
**Backend**: Django REST/FastAPI | **Database**: PostgreSQL/SQLite | **Testing**: pytest | **Frontend**: React/Vue/Django templates

### Option 2: Java
**Backend**: Spring Boot | **Database**: PostgreSQL/H2 | **Testing**: JUnit5 + Mockito | **Frontend**: React/Thymeleaf

### Option 3: Node.js
**Backend**: Express/NestJS | **Database**: MongoDB/PostgreSQL | **Testing**: Jest/Mocha | **Frontend**: React/Vue/EJS

### Option 4: Other
Use any language/framework of your choice - focus on the functionality, not the stack.

---

## Development Workflow Phases

Follow these phases in order for successful completion:

1. **Requirement Document** - Define functional and non-functional requirements for the API
2. **Plan** - Design database schema, API structure, and data relationships
3. **Instructions** - Write implementation guide for your chosen tech stack
4. **Prompts** - Define prompts to assist with API generation
5. **Chat Participants and Variables** - Set up collaboration context and variables
6. **Agents** - Configure any custom agents for your domain
7. **Custom Agent** - Create specialized agent for REST API development patterns
8. **Generating Code Using Agent/Custom Agent** - Generate project scaffold and models
9. **API Generation** - Implement all REST endpoints with proper validation
10. **UI Generation** - Build frontend for product browsing, filtering, and CRUD operations
11. **Unit Test Cases** - Write unit tests for controllers, services, and repositories
12. **Automation Testing** - Implement integration and end-to-end API tests
13. **Documentation** - Create API docs, user guides, and technical documentation

---

## Expected Deliverables

- ✅ **Source Code** in `/src` folder (organized by layers: model, repository, service, controller)
- ✅ **Test Suite** with unit and integration tests (min 70% coverage)
- ✅ **API Documentation** in `/docs/API.md` (endpoints, request/response examples, error codes)
- ✅ **User Guide** in `/docs/USER_GUIDE.md` (how to use the API)
- ✅ **Technical Documentation** in `/docs/TECHNICAL.md` (architecture, design decisions)
- ✅ **Database Schema** in `/docs/DATABASE_SCHEMA.md` (tables, relationships, indexes)
- ✅ **Sample Data** in `/data/sample.json` (test data for initial load)

---

## Validation Criteria

Your solution will be validated against:

- ✅ **App Must Be Running** - API server starts without errors, all endpoints accessible
- ✅ **Tests Must Be Passing** - 100% of unit and integration tests pass with >70% code coverage
- ✅ **Exceptions/Errors Must Be Handled** - Proper HTTP status codes and error messages for invalid requests
- ✅ **Documents Must Be Present in /docs Folder** - Complete API documentation, user guide, and technical architecture
- ✅ **Source Code Must Be Present in /src Folder** - Well-organized code with proper layering and separation of concerns

---

## Challenge Extension Ideas (If Time Permits)

- Implement product ratings and reviews system
- Add discount/coupon functionality
- Create product recommendations based on category
- Implement bulk product import from CSV
- Add pagination with cursor-based navigation
- Implement caching for frequently accessed products
- Add authentication and role-based access control
- Implement product versioning and audit logs
- Add image/media upload support for products

---

**END OF CHALLENGE 2**
