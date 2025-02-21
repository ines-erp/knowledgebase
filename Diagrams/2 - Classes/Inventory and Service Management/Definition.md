## Item (Must)
Is the base class that will be extended into Service and Product

### Attributes:
- itemId (Unique identifier)
- sku (Stock Keeping Unit)
  - Is a unique identifier to specific product based on their attributes, they are alphanumeric and human-readable, eg: "TSHIRT-BLUE-L"
- name
- description
- categoryId (Foreign key to CategoryItem)
- cost
- price
  - This by default could be 0, for items that are not for sale be are part of the inventory of the client
- isActive (Boolean to indicate if the item is active)
- isForSale (Boolean to indicate if the item is for Sale)

## Product (Must)
Extends the class Item

### Attributes
- type
  - the type indicates if the product is a consumable, is a resource or is a sale product
- stockLevel
  - the current level for that product
- minimumStockLevel
  - minimum stock allowed, if that number is reached the system will trigger some behaviours.
- maximumStockLevel (opposite of minimum, same behaviour)
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
- productRequired (List of products needed, could be from type resources or consumables, e.g., tools, staff, cleaning supplies, spare parts))

## ItemCategory (should)
This will be extended from the main class Category
### Attributes:
- categoryId (Unique identifier)
- name
- description

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
This must implement the main class Transaction
### Attributes:
- transactionId (Unique identifier)
- itemId (Foreign key to Product)
- responsibleParty (e.g: Foreign key to Warehouse)
- transactionType (e.g., "Purchase", "Sale", "Transfer", "Adjustment")
- quantity
- transactionDate
- relatedOrderId (Optional, e.g., Purchase Order ID or Sales Order ID)
- notes

### Methods:
- logTransaction()

## Report (could)
This also mus implement the default report class
### Attributes:
- reportId (Unique identifier)
- reportType (e.g., "Stock Movement", "Aging Analysis", "Inventory Valuation", "Services done")
- generatedDate
- parameters (Criteria used to generate the report)

### Methods:
- generateReport()
- exportReport(format) (e.g., PDF, Excel)

