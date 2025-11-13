# Odoo 18 Golden Stars Management System - Developer Guide

## 📋💡 Overview 
This custom module provides the customized business logic and views required to manage the operational flow of Golden Start Tyres. Golden Start Tyres is a retail shop that specializes in selling tyres of all models and sizes. This Odoo module acts as the central system for key business processes, extending standard Odoo functionalities to cater to the automotive tyre retail sector.

## 🎯 Core Objectives Project Phases & Module Structure
- Manage everyday tyre sales 
- Track tyre inventory (Stock in and out)
- Manage suppliers purchases
---

## 🏗️⚙️ Module Structure & Technical Details

### Module Name
Technical Name: `tyre_management`
Prefix Standard: gtm_ (Used for all custom fields and methods)

### Dependencies
```python
'depends': [
    'base',
    'sales_management',   # Sales 
    'purchase',           # Purchases 
    'inventory',          # Inventory Management 
]
```
---
## 📦 Phase 1: Sales Record (Priority: High 🥇)

**Purpose**: Ensure complete and accurate recording of all tyre sales and related services.

# 🎯 Goal 
Ensure complete and accurate recording of all tyre sales and related services.

# ⚙️ Sales Module Extensions 
**Key Fields**:
```python
- sale_number (Char) - Auto-generated unique ID
- Creation (Date) - When sale was created 
- customer_name (Char) - Required
- tyre_type - model of the tyre name
- size - the size of the tyre etc. R15 or R14
- amount - amount paid by the customer 
- Status - if the amount was paid in full or partial payment
```

**Workflow States**:
1. **Posted** - Amount paid in full
2. **Partial** - Amount paid partial
---

## Phase 2: Inventory Tracking (Priority: Medium 📦)

**Purpose**: Focuses on detailed stock movement tracking, especially related to the unique attributes of tyres

# 🎯 Goal
Achieve real-time, accurate visibility of stock levels and movement, linking serial numbers to specific sales/purchases

## Phase 3: Track Purchase (Priority: Medium 💰)
Focuses on recording purchases from suppliers (purchase.order) and linking them directly to incoming stock (stock-in)

# 🎯 Goal
Streamline procurement, ensure supplier info is recorded, and accurately link purchases to stock receipts

## 🚀📅 Implementation Roadmap

### Sprint 1
- [ ] Envirnment Setup
- [ ] Create module structure
- [ ] Implement Tyres model
- [ ] Implement Class model
- [ ] Basic security groups
- [ ] Dependency Configuration

### Sprint 2
- [ ] Sales Record development 
- [ ] product extensions
- [ ] Core methods

### Sprint 3
- [ ] Inventory configuration (Lots/Serials)
- [ ] stock movement customization
- [ ] Valuation Logic

### Sprint 4
- [ ] Purchase extensions
- [ ] Supplier SKU tracking
- [ ] Automated stock receipt

### Sprint 5 (Weeks 9-10): Polish & Testing
- [ ] Complete all views
- [ ] User Acceptance Testing
- [ ] Final code refinement
- [ ] Testing and bug fixes

---

## 🧪 Testing Checklist

- [ ] Create a new tyre product, ensuring all gtm_ fields are correctly displayed and saved
- [ ] Create a sales order for a tyre, confirming the gtm_serial_number is captured and linked to the final delivery
- [ ] Check the 'Quantity On Hand' for a specific tyre model after a purchase receipt
- [ ] Create a purchase order, confirm it, and receive the tyres into stock. Verify the gtm_supplier_sku is saved
- [ ] Verify the single user can access, modify, and delete records across all three phases

---

## 📝 Important Notes

1. **Stock-In/Stock-Out**: Odoo handles Stock-In via Purchase Receipts and Stock-Out via Sales Deliveries/Scrap; no custom core models needed, only extensions on the forms.
2. **Data Migration**: A plan must be established to migrate existing product data and populate the new gtm_ specification fields before Go-Live. 
3. **Data Validation**: Implement constraints (unique sale, purchase, inventory IDs, valid dates, etc.)
4. **Audit Trail**: Track all state changes for applications, admissions, and payments

---

## 🔗 Useful Odoo Documentation Links

- Models: https://www.odoo.com/documentation/18.0/developer/howtos/backend.html%23how-to-create-an-odoo-module
- Views: https://www.odoo.com/documentation/18.0/developer/reference/backend/views.html
- Security: https://www.odoo.com/documentation/18.0/developer/reference/backend/security.html
- Accounting Integration: https://www.odoo.com/documentation/18.0/applications/finance/accounting.html

---

**Version**: 1.0  
**Last Updated**: November 2025  
**Odoo Version**: 19.0
