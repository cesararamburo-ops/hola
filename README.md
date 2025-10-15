```mermaid
erDiagram
  ARRIVED_RETURN_LABELS {
    string id PK
    string scanned_return_label
    string scan_at
    string scan_end_at
    string return_completed_at
    string scanned_by_id
    string return_id
    string shipping_label_id
    string warehouse_id
    string created_at
    string updated_at
    string carrier_name
  }
  CLAIMS {
    string id PK
    string order_id
    string status
    string description
    string value
    string resolved_at
    string resolution
    string resolved_by_id
    string created_by_id
    string created_at
    string updated_at
    string area
    string category
    string accepted_value
    string motive
    string recommendation
    string reimbursables
    string claim_message
    string claimed_products_value
    string requested_value
  }
  ORDERS {
    string id PK
    string store_id
    string warehouse_id
    string order_number
    string status
    string shipping_zip_code
    string shipping_method_id
    string delivered_at
    string first_delivery_attempt_at
    string shipping_date
  }
  STORES {
    string id PK
    string name
    string created_at
    string updated_at
  }
  USERS {
    string id PK
    string first_name
    string last_name
    string email
    string is_enabled
  }
  PRODUCTS {
    string id PK
    string store_id
    string name
    string price
    string weight
  }
  SHIPPING_LABELS {
    string id PK
    string order_id
    string shipping_number
    string shipping_method_id
    string created_at
  }
  SHIPPING_METHODS {
    string id PK
    string carrier_name
    string is_active
  }
  SHIPPING_COVERAGES {
    string id PK
    string shipping_method_id
    string value
    string enabled
  }
  ZIP_CODE_METADATA {
    string zip_code PK
    string state
    string city
  }
  ORDER_LINES {
    string id PK
    string order_id
    string product_id
    string quantity
    string price_per_item
  }
  RETURNS {
    string id PK
    string returned_order_id
    string created_at
  }

  -- Relaciones principales (muchos a uno)
  ORDERS ||--o{ SHIPPING_LABELS : order_id
  ORDERS ||--o{ ORDER_LINES : order_id
  ORDERS ||--o{ CLAIMS : order_id
  ORDERS ||--o{ RETURNS : returned_order_id
  STORES ||--o{ ORDERS : store_id
  WAREHOUSES ||--o{ ORDERS : warehouse_id
  PRODUCTS ||--o{ ORDER_LINES : product_id
  SHIPPING_METHODS ||--o{ SHIPPING_LABELS : shipping_method_id
  SHIPPING_METHODS ||--o{ SHIPPING_COVERAGES : shipping_method_id
  USERS ||--o{ SHIPPING_INCIDENTS : created_by_id
  ZIP_CODE_METADATA }o--o{ SHIPPING_COVERAGES : value -> zip_code_metadata.zip_code
  ZIP_CODE_METADATA }o--o{ ORDERS : shipping_zip_code -> zip_code_metadata.zip_code
```
