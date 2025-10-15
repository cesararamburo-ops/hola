# ERD (Consultas frecuentes)

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
  INTEGRATION_SHIPPING_METHODS {
    string id PK
    string channel_integration_id
    string name
    string code
    string shipping_type
    string created_at
    string updated_at
    string shipping_group_id
    string status
    string match_type
  }
  NCM_CONFIGURATIONS {
    string id PK
    string store_id
    string ncm
    string description
    string cfop_tax_situation
    string cfop_sym_return_invoice_same_state
    string cfop_sym_return_invoice_other_state
    string cfop_sale_invoice_same_state
    string cfop_sale_invoice_other_state
    string cfop_donation_invoice_same_state
    string cfop_donation_invoice_other_state
    string cfop_replenishment_invoice_same_state
    string cfop_replenishment_invoice_other_state
    string cfop_replenishment_adjustment_invoice_same_state
    string cfop_return_invoice
    string cfop_donation_return_invoice_same_state
    string cfop_donation_return_invoice_other_state
    string ipi_tax_situation
    string ipi_framing_code
    string ipi_tax_rate
    string pis_tax_situation
    string pis_tax_rate
    string cofins_tax_situation
    string cofins_tax_rate
    string exception_ncm_variant
    ...
  }
  ORDER_ETA_HISTORIES {
    string id PK
    string order_id
    string order_status
    string shipping_method_id
    string shipping_zip_code
    string estimated_time_arrival
    string max_estimated_time_arrival
    string eta_margin_of_error_in_hours
    string used_dispatch_time
    string is_dispatch_eta
    string eta_update_reason
    string created_at
    string delivery_sla
    string is_first_eta
    string used_algorithm
  }
  ORDER_HISTORIES {
    string id PK
    string order_id
    string created_by_id
    string previous_status
    string new_status
    string action
    string metadata
    string origin
    string reference_timestamp
    string created_at
    string updated_at
  }
  ORDER_LINES {
    string id PK
    string product_id
    string order_id
    string channel_product_id
    string external_json
    string sku
    string quantity
    string name
    string created_at
    string updated_at
    string missing_info
    string has_missing_info
    string generated
    string price_per_item
    string discount_per_item
    string integration_price_per_item
    string integration_discount_per_item
  }
  ORDERS {
    string id PK
    string channel_integration_id
    string store_id
    string channel_json
    string channel_order_id
    string order_number
    string notes
    string channel_created_at
    string channel_updated_at
    string order_date
    string shipping_date
    string status
    string shipping_address
    string shipping_sha256
    string shipping_first_name
    string shipping_last_name
    string shipping_company
    string shipping_address_1
    string shipping_address_2
    string shipping_email
    string shipping_zip_code
    string shipping_country
    string shipping_state
    string shipping_city
    string billing_address
    ...
  }
  PRODUCTS {
    string id PK
    string store_id
    string parent_id
    string name
    string description_html
    string status
    string weight
    string weight_unit
    string grams
    string price
    string is_kit?
    string created_at
    string updated_at
    string bar_code
    string options
    string options_name
    string is_dropshipping
    string channel_product_id
    string billing_name
    string has_imei
    string is_fragile
    string is_scannable
    string discarded_at
    string is_parent
    string has_expiration
    ...
  }
  RETURNS {
    string id PK
    string returned_order_id
    string replenishment_id
    string created_order_id
    string resolved_at
    string notes
    string status
    string resolved_by_id
    string created_by_id
    string created_at
    string updated_at
    string expected_products
    string return_type
    string exchange_products
    string externally_requested
    string store_id
    string pickup_at_home
  }
  SHIPPING_COSTS {
    string id PK
    string shipping_method_id
    string max_compound_weight
    string cost
    string currency_code
    string tarif_zone
    string created_at
    string updated_at
    string coverage_enabled
  }
  SHIPPING_COVERAGE_BILLING_CATEGORIES {
    string id PK
    string shipping_method_id
    string postcode_range
    string category
    string created_at
    string updated_at
  }
  SHIPPING_COVERAGES {
    string id PK
    string shipping_method_id
    string value
    string created_at
    string updated_at
    string zone
    string extended_zone
    string po_box_dropoff
    string content_value_fee
    string enabled
    string delivery_sla_in_hours
    string delivery_sla_offset
    string eta_offset
    string fee_offset
  }
  SHIPPING_INCIDENTS {
    string id PK
    string order_id
    string status
    string category
    string description
    string resolution
    string created_by_id
    string resolved_by_id
    string resolved_at
    string created_at
    string updated_at
    string origin
  }
  SHIPPING_LABELS {
    string id PK
    string order_id
    string shipping_method_id
    string label_url
    string price
    string shipping_type
    string shipping_number
    string package
    string created_at
    string updated_at
    string tracking_url
    string status
    string label_type
    string created_by_id
    string service_id
    string shipping_package_id
    string dispatched_at
    string package_weight
    string warehouse_packing_material_id
    string cost
    string last_tracking_checked_at
    string volumetric_weight_kg
    string physical_weight_kg
  }
  SHIPPING_METHOD_GROUPS {
    string id PK
    string shipping_method_id
    string shipping_group_id
    string group_role
    string created_at
    string updated_at
  }
  SHIPPING_METHODS {
    string id PK
    string shipping_name
    string carrier_name
    string shipping_type
    string created_at
    string updated_at
    string delivery_type
    string country
    string is_cod
    string is_active
    string contract_provider
    string extended_zone
    string po_box_dropoff
    string non_working_days
    string provides_pod
    string enable_multipackage
    string dispatch_carrier_alias
  }
  STORE_BILLING_SERVICE_USAGES {
    string id PK
    string billing_service_id
    string billable_type
    string billable_id
    string billed_usage
    string billed_total_price
    string billed_details
    string statement_id
    string created_at
    string invalidated_at
    string refunded_by_id
    string marketplace_related
  }
  STORE_BILLING_SERVICES {
    string id PK
    string store_id
    string warehouse_id
    string store_billing_configuration_id
    string service_type
    string price_configuration
    string currency
    string created_at
    string updated_at
    string service_type_category
    string custom_service_details
    string updated_by_id
  }
  STORES {
    string id PK
    string name
    string description
    string created_at
    string updated_at
    string account_id
    string created_by_id
    string tax_id
    string state
    string tax_regime
    string tax_company_name
    string tax_address
    string tax_address_number
    string tax_address_neighborhood
    string tax_city
    string tax_zipcode
    string tax_state_registration
    string tax_state_phone
    string invoice_customization
    string store_type
    string enable_replenishment_invoices
  }
  USERS {
    string id PK
    string auth0_uid
    string email
    string first_name
    string last_name
    string created_at
    string updated_at
    string roles
    string default_store_id
    string is_enabled
    string shift
    string squad
  }
  WAREHOUSE_DISPATCH_SCHEDULES {
    string id PK
    string warehouse_id
    string carrier_name
    string dispatch_day
    string dispatch_time
    string time_before_dispatch
    string enable
    string created_at
    string updated_at
  }
  WAREHOUSES {
    string id PK
    string unique_code
    string name
    string address1
    string zip_code
    string city
    string country
    string created_at
    string updated_at
    string address2
    string state
    string phone
    string number
    string neighborhood
    string invoicing_id
    string invoicing_company
    string invoicing_company_registration_number
    string invoicing_address_street
    string invoicing_address_number
    string invoicing_address_city
    string invoicing_address_state
    string invoicing_address_neighborhood
    string invoicing_address_zipcode
    string invoicing_address_phone
    string time_zone
    ...
  }
  ZIP_CODE_METADATA {
    string id PK
    string zip_code
    string city
    string municipality
    string state
    string state_abbreviation
    string state_abbreviation_two_letters
    string state_renapoa
    string state_iso31662
    string country
    string created_at
    string updated_at
  }
  STORES ||--o{ ORDERS : store_id
  WAREHOUSES ||--o{ ORDERS : warehouse_id
  SHIPPING_METHODS ||--o{ ORDERS : shipping_method_id
  ORDERS ||--o{ SHIPPING_LABELS : order_id
  SHIPPING_METHODS ||--o{ SHIPPING_LABELS : shipping_method_id
  ORDERS ||--o{ ORDER_HISTORIES : order_id
  ORDERS ||--o{ SHIPPING_INCIDENTS : order_id
  SHIPPING_METHODS ||--o{ SHIPPING_COSTS : shipping_method_id
  SHIPPING_METHODS ||--o{ SHIPPING_COVERAGES : shipping_method_id
  SHIPPING_METHODS ||--o{ SHIPPING_COVERAGE_BILLING_CATEGORIES : shipping_method_id
  SHIPPING_METHODS ||--o{ SHIPPING_METHOD_GROUPS : shipping_method_id
  PRODUCTS ||--o{ ORDER_LINES : product_id
  ORDERS ||--o{ ORDER_LINES : order_id
  STORES ||--o{ PRODUCTS : store_id
  NCM_CONFIGURATIONS ||--o{ PRODUCTS : ncm_configuration_id
  WAREHOUSES ||--o{ WAREHOUSE_DISPATCH_SCHEDULES : warehouse_id
  ORDERS ||--o{ CLAIMS : order_id
  RETURNS ||--o{ ARRIVED_RETURN_LABELS : return_id
  SHIPPING_LABELS ||--o{ ARRIVED_RETURN_LABELS : shipping_label_id
  WAREHOUSES ||--o{ ARRIVED_RETURN_LABELS : warehouse_id
  STORES ||--o{ RETURNS : store_id
  ORDERS ||--o{ ORDER_ETA_HISTORIES : order_id
  SHIPPING_METHODS ||--o{ ORDER_ETA_HISTORIES : shipping_method_id
  STORES ||--o{ NCM_CONFIGURATIONS : store_id
  STORES ||--o{ STORE_BILLING_SERVICES : store_id
  WAREHOUSES ||--o{ STORE_BILLING_SERVICES : warehouse_id
  USERS ||--o{ SHIPPING_INCIDENTS : created_by_id
  ORDERS ||--o{ RETURNS : returned_order_id
  ZIP_CODE_METADATA }o--o{ SHIPPING_COVERAGES : value -> zip_code_metadata.zip_code
  ZIP_CODE_METADATA }o--o{ ORDERS : shipping_zip_code -> zip_code_metadata.zip_code
```
