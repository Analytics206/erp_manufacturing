# ERP Manufacturing
| [README.md](README.md) | Return to project details README.md |

```YAML
                                 [Users]──┬────────────────────────────┐
                                        │                            │
                                        ▼                            ▼
   [WorkCenters] ───→ [Machines] ──→ [Customers]───┬─── [Estimates] ─────→ [Jobs]──────────┐
                                        │         │
                                        ▼         ▼
                    [CustomerShippingAddresses] [CustomerBillingAddresses]
        │                                │                             │               │
        │                                │                             │               │
        ▼                                ▼                             ▼               │
 [ProductionOrders]──→ [Operations] ─→ [Invoices]               [TimeEntries]         │
        │                 │               │                             │               │
        │                 │               ▼                             ▼               ▼
        ▼                 └─────→ [Payments]                     [Employees]      [MaterialRequirements]
  [QualityInspections]                   │                                                 │
                                         ▼                                                 ▼
                     [Vendors] ─────→ [InventoryItems] ──┬────→ [PurchaseOrders]      [BillOfMaterials]
                                                        │
                                                        ▼
                                                   [StockMovements]
```

# Entity Descriptions
### 🧑‍💼 Users
- id (PK)
- name
- email
- role (e.g. admin, manager, operator, quality_inspector)
- permissions (JSON field for granular permissions)
- password_hash
- active
- is_deleted (boolean for soft delete)
- last_login_at
- created_at
- updated_at

### 🏢 Customers
- id (PK)
- user_id (FK → Users)
- name
- email
- phone
- notes
- is_active
- is_deleted (boolean for soft delete)
- created_at
- updated_at

### 📍 CustomerShippingAddresses
- id (PK)
- customer_id (FK → Customers)
- address_line_1
- address_line_2
- city
- state
- postal_code
- country
- contact_name
- contact_phone
- is_default
- is_active
- notes
- created_at
- updated_at

### 📍 CustomerBillingAddresses
- id (PK)
- customer_id (FK → Customers)
- address_line_1
- address_line_2
- city
- state
- postal_code
- country
- contact_name
- contact_phone
- is_default
- is_active
- notes
- created_at
- updated_at

### 📋 Estimates
- id (PK)
- estimate_number
- customer_id (FK → Customers)
- user_id (FK → Users)
- description
- status (e.g. Draft, Sent, Accepted, Rejected)
- valid_until_date
- amount
- currency
- is_deleted (boolean for soft delete)
- notes
- created_at
- updated_at

### 🛠 Jobs
- id (PK)
- job_number
- estimate_id (FK → Estimates, nullable)
- customer_id (FK → Customers)
- title
- description
- priority (High, Medium, Low)
- status (Planned, In Progress, On Hold, Quality Check, Ready, Delivered)
- budget
- actual_cost
- completion_percentage
- start_date
- due_date
- end_date
- is_deleted (boolean for soft delete)
- created_by (FK → Users)
- created_at
- updated_at

### 📆 TimeEntries
- id (PK)
- job_id (FK → Jobs)
- employee_id (FK → Employees)
- hours
- description
- date
- login_time
- logout_time
- created_at
- updated_at

### 🧑‍🔧 Employees
- id (PK)
- name
- position
- email
- phone
- active
- created_at
- updated_at

### 📦 InventoryItems
- id (PK)
- vendor_id (FK → Vendors, nullable)
- name
- description
- sku
- barcode
- stock_quantity
- minimum_stock_level
- reorder_point
- unit_price
- cost_price
- currency
- category
- location
- is_raw_material (boolean)
- is_finished_product (boolean)
- is_active
- is_deleted (boolean for soft delete)
- lead_time_days
- created_at
- updated_at

### 🧾 Invoices
- id (PK)
- invoice_number
- customer_id (FK → Customers)
- job_id (FK → Jobs)
- total_amount
- tax_amount
- currency
- status (Draft, Sent, Unpaid, Partially Paid, Paid, Overdue, Canceled)
- issue_date
- due_date
- notes
- is_deleted (boolean for soft delete)
- created_by (FK → Users)
- created_at
- updated_at

### 💸 InvoiceLineItems
- id (PK)
- invoice_id (FK → Invoices)
- description
- inventory_item_id (FK → InventoryItems, nullable)
- quantity
- unit_price
- discount_percentage
- tax_rate
- total
- created_at
- updated_at

### 💸 Payments
- id (PK)
- payment_number
- invoice_id (FK → Invoices)
- amount
- payment_date
- method (Card, Bank, Check)
- created_at
- updated_at

### 🏭 Vendors
- id (PK)
- vendor_number
- name
- contact_name
- phone
- email
- address
- active
- created_at
- updated_at

### 📥 PurchaseOrders
- id (PK)
- po_number
- vendor_id (FK → Vendors)
- total_amount
- currency
- order_date
- expected_delivery_date
- actual_delivery_date
- status (Draft, Submitted, Approved, Shipped, Received, Canceled)
- notes
- approval_user_id (FK → Users, nullable)
- is_deleted (boolean for soft delete)
- created_by (FK → Users)
- created_at
- updated_at

### 📊 PurchaseOrderItems
- id (PK)
- purchase_order_id (FK → PurchaseOrders)
- inventory_item_id (FK → InventoryItems)
- quantity
- unit_price
- total_price
- received_quantity
- expected_delivery_date
- created_at
- updated_at

### 🔄 StockMovements
- id (PK)
- inventory_item_id (FK → InventoryItems)
- quantity_change (positive or negative)
- reason (e.g., usage, restock, adjustment, transfer, quality_issue)
- reference_type (e.g., Job, PO, Adjustment)
- reference_id (polymorphic reference to related entity)
- from_location (for transfers)
- to_location (for transfers)
- date
- notes
- performed_by (FK → Users)
- created_at
- updated_at

### 🔧 Machines
- id (PK)
- name
- model
- work_center_id (FK → WorkCenters)
- status (Operational, Maintenance, Down)
- maintenance_schedule
- last_maintenance_date
- next_maintenance_date
- hourly_rate
- notes
- is_active
- created_at
- updated_at

### 🏭 WorkCenters
- id (PK)
- name
- description
- location
- manager_id (FK → Users, nullable)
- capacity_per_day
- is_active
- created_at
- updated_at

### 📋 ProductionOrders
- id (PK)
- production_number
- job_id (FK → Jobs)
- status (Planned, In Progress, Completed, On Hold, Canceled)
- quantity_ordered
- quantity_produced
- start_date
- completion_date
- priority
- notes
- created_by (FK → Users)
- created_at
- updated_at

### ⚙️ Operations
- id (PK)
- production_order_id (FK → ProductionOrders)
- work_center_id (FK → WorkCenters)
- machine_id (FK → Machines, nullable)
- name
- description
- sequence_number
- status (Pending, In Progress, Completed, On Hold)
- standard_time_minutes
- actual_time_minutes
- start_time
- end_time
- notes
- created_at
- updated_at

### 📦 MaterialRequirements
- id (PK)
- job_id (FK → Jobs)
- inventory_item_id (FK → InventoryItems)
- required_quantity
- allocated_quantity
- consumed_quantity
- created_at
- updated_at

### 📑 BillOfMaterials
- id (PK)
- product_id (FK → InventoryItems)
- component_id (FK → InventoryItems)
- quantity_required
- unit_of_measure
- version
- is_active
- notes
- created_at
- updated_at

### 🔍 QualityInspections
- id (PK)
- production_order_id (FK → ProductionOrders)
- operation_id (FK → Operations, nullable)
- inspector_id (FK → Users)
- status (Pending, Passed, Failed, Waived)
- inspection_date
- checklist_items (JSON field for inspection points)
- defects_found
- resolution
- notes
- created_at
- updated_at

### 🧾 AuditLog
- id (PK)
- user_id (FK → Users)
- action_type (Create, Update, Delete, Login, etc.)
- entity_type (table name)
- entity_id
- changes (JSON field containing before/after values)
- ip_address
- created_at

### 🔗 Relationship Summary
| From	| To	| Relationship |
| --- | --- | --- |
| Users	| Customers	| One-to-Many |
| Customers	| CustomerShippingAddresses	| One-to-Many |
| Customers	| CustomerBillingAddresses	| One-to-Many |
| Users	| Estimates	| One-to-Many |
| Customers	| Estimates	| One-to-Many |
| Estimates	| Jobs	| One-to-Many |
| Customers	| Jobs	| One-to-Many |
| Jobs	| TimeEntries	| One-to-Many |
| Employees	| TimeEntries	| One-to-Many |
| Customers	| Invoices	| One-to-Many |
| Jobs	| Invoices	| One-to-Many |
| Invoices	| InvoiceLineItems	| One-to-Many |
| Invoices	| Payments	| One-to-Many |
| Vendors	| InventoryItems	| One-to-Many |
| Vendors	| PurchaseOrders	| One-to-Many |
| PurchaseOrders	| PurchaseOrderItems	| One-to-Many |
| PurchaseOrderItems	| InventoryItems	| Many-to-One |
| InventoryItems	| StockMovements	| One-to-Many |
| WorkCenters	| Machines	| One-to-Many |
| Jobs	| ProductionOrders	| One-to-Many |
| ProductionOrders	| Operations	| One-to-Many |
| WorkCenters	| Operations	| One-to-Many |
| Machines	| Operations	| One-to-Many |
| Jobs	| MaterialRequirements	| One-to-Many |
| InventoryItems	| MaterialRequirements	| One-to-Many |
| InventoryItems	| BillOfMaterials	| One-to-Many (as product) |
| InventoryItems	| BillOfMaterials	| One-to-Many (as component) |
| ProductionOrders	| QualityInspections	| One-to-Many |
| Operations	| QualityInspections	| One-to-Many |
| Users	| QualityInspections	| One-to-Many |
| Users	| AuditLog	| One-to-Many |