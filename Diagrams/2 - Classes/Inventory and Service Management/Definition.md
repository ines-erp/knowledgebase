## Item (Must)
Is the base class that will be extended into Service and Product

### Attributes:
- itemId (Unique identifier)
- sku (Stock Keeping Unit)
  - Is a unique identifier to specific product based on their attributes, they are alphanumeric and human-readable, eg: "TSHIRT-BLUE-L"
- name
- description
- categoryId (Foreign key to Category)
- cost
- price
- isActive (Boolean to indicate if the item is active)

## Product (Must)
Extends the class Item

### Attributes
- stockLevel
- minimumStockLevel
- maximumStockLevel
- batchNumber (Optional, for batch tracking)
- expiryDate (Optional, for perishable items)
### Methods:
- updateStockLevel(quantity)
- checkLowStock()
- checkOverstock()

## Service (Must)
Extends the class Item

### Attributes
- duration
- resourcesRequired (List of resources needed, e.g., tools, staff)
- consumablesRequired (List of consumables that are items used during service delivery (e.g., cleaning supplies, spare parts).)

## Resource (should)
   Definition: Resources are the tools, equipment, or staff required to deliver a service.

### Attributes:
- resourceId (Unique identifier)
- name (e.g., "Technician," "Diagnostic Tool")
- type (e.g., "Human," "Equipment")
- availability (e.g., "Available," "In Use")
- cost (Cost associated with the resource, e.g., hourly wage or rental fee)

## Consumable (should)
Definition: Consumables are items used during service delivery (e.g., cleaning supplies, spare parts).

### Attributes:
- consumableId (Unique identifier)
- name (e.g., "Air Filter")
- description (e.g., "Replacement air filter for HVAC systems")
- stockLevel (Quantity in stock)
- cost (Cost per unit)

## Category (should)
### Attributes:
- categoryId (Unique identifier)
- name
- description

### Methods:
- addItem(itemId)
- removeItem(itemId)

## Group (Product Bundles/Kits or Service Bundles) (could)
### Attributes:
- groupId (Unique identifier)
- name
- description
- items (List of item objects or IDs)

### Methods:
- addItem(itemId)
- removeItem(itemId)

## Warehouse (could)
### Attributes:
- warehouseId (Unique identifier)
- name
- location
- contactPerson
- isActive (Boolean to indicate if the warehouse is active)

### Methods:
- getStockLevel(itemId)
- transferStock(itemId, quantity, destinationWarehouseId)

## StockTransaction (could)
### Attributes:
- transactionId (Unique identifier)
- itemId (Foreign key to Product)
- warehouseId (Foreign key to Warehouse)
- transactionType (e.g., "Purchase", "Sale", "Transfer", "Adjustment")
- quantity
- transactionDate
- relatedOrderId (Optional, e.g., Purchase Order ID or Sales Order ID)
- notes

### Methods:
- logTransaction()

## Report (could)
### Attributes:
- reportId (Unique identifier)
- reportType (e.g., "Stock Movement", "Aging Analysis", "Inventory Valuation", "Services done")
- generatedDate
- parameters (Criteria used to generate the report)

### Methods:
- generateReport()
- exportReport(format) (e.g., PDF, Excel)

