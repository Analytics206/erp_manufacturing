# ERP Manufacturing
```YAML
[Users]──┬────────────────────────────┐
        │                            │
        ▼                            ▼
   [Customers] ←──── [Estimates] ─────→ [Jobs]
        │                             │
        │                             │
        ▼                             ▼
  [Invoices]                    [TimeEntries]
        │                             │
        ▼                             ▼
    [Payments]                  [Employees]
        │                             │
        ▼                             ▼
    [Vendors] ─────→ [InventoryItems] ──┬────→ [PurchaseOrders]
                                       │
                                       ▼
                                  [StockMovements]
```

# Entity Descriptions
## 🧾 Entity Descriptions
### 🧑‍💼 Users
- id (PK)
- name
- email
- role (e.g. admin, manager)
- password_hash
- created_at
- active

### 🏢 Customers
- id (PK)
- user_id (FK → Users)
- name
- email
- phone
- billing_address
- shipping_address
- created_at

### 📋 Estimates
- id (PK)
- customer_id (FK → Customers)
- user_id (FK → Users)
- description
- status (e.g. Draft, Sent, Accepted)
- amount
- created_at

### 🛠 Jobs
- id (PK)
- estimate_id (FK → Estimates)
- customer_id (FK → Customers)
- title
- status (In Progress, Review, Ready)
- budget
- completion_percentage
- start_date
- end_date

### 📆 TimeEntries
- id (PK)
- job_id (FK → Jobs)
- employee_id (FK → Employees)
- hours
- description
- date

### 🧑‍🔧 Employees
- id (PK)
- name
- position
- email
- phone

### 📦 InventoryItems
- id (PK)
- vendor_id (FK → Vendors)
- name
- sku
- stock_quantity
- minimum_stock_level
- unit_price
- category

### 🧾 Invoices
- id (PK)
- customer_id (FK → Customers)
- job_id (FK → Jobs)
- amount
- status (Unpaid, Paid, Overdue)
- due_date
- created_at

### 💸 Payments
- id (PK)
- invoice_id (FK → Invoices)
- amount
- payment_date
- method (Card, Bank, Check)

### 🏭 Vendors
- id (PK)
- name
- contact_name
- phone
- email
- address

### 📥 PurchaseOrders
- id (PK)
- vendor_id (FK → Vendors)
- inventory_item_id (FK → InventoryItems)
- quantity
- cost
- order_date
- status

### 🔄 StockMovements
- id (PK)
- inventory_item_id (FK → InventoryItems)
- quantity_change (positive or negative)
- reason (e.g., usage, restock)
- date
- related_job_id (nullable FK → Jobs)

### 🔗 Relationship Summary
| From	| To	| Relationship |
| --- | --- | --- |
| Users	| Customers	| One-to-Many |
| Users	| Estimates	| One-to-Many |
| Customers	| Estimates	| One-to-Many |
| Estimates	| Jobs	| One-to-One (nullable) |
| Customers	| Jobs	| One-to-Many |
| Jobs	| TimeEntries	| One-to-Many |
| Employees	| TimeEntries	| One-to-Many |
| Customers	| Invoices	| One-to-Many |
| Jobs	| Invoices	| One-to-Many |
| Invoices	| Payments	| One-to-Many |
| Vendors	| InventoryItems	| One-to-Many |
| Vendors	| PurchaseOrders	| One-to-Many |
| InventoryItems	| PurchaseOrders	| One-to-Many |
| InventoryItems	| StockMovements	| One-to-Many |