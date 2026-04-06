# Instagram Thrift & Handmade Store — Database Design (ER Diagram)

This repository contains the Entity-Relationship (ER) diagram for a small Instagram-based store that sells **thrifted fashion items** and **handmade products**. The database design supports product management, inventory tracking, customer orders, payments, and shipping.

## Problem Overview

The store started by receiving orders through Instagram DMs and WhatsApp. As it grew, the owner needed a proper system to:

- Track what products are available (thrifted vs handmade)
- Manage stock (unique pieces vs multi-unit inventory)
- Handle customer orders with multiple items
- Track payment and shipping status per order
- Store customer details and order history


## Entities 

 + `CUSTOMER` - Stores buyer info: name, phone, email, Instagram handle, address 
 + `ORDER` - One customer can place many orders; tracks status and total amount 
 + `ORDER_ITEM` -  Junction table: links orders to products; stores quantity and price at time of purchase 
 + `PRODUCT` - Core catalog entity; stores name, price, category, size, color, condition, image 
 + `PRODUCT_TYPE` - Distinguishes thrifted vs handmade; includes `is_unique` flag 
 + `INVENTORY` - Tracks stock per product: total, reserved, and available units 
 + `PAYMENT` - Linked to an order; stores method, status, and transaction reference 
 + `SHIPPING` - Linked to an order; stores courier, tracking number, and delivery timestamps 

---

## Relationships & Cardinality


 + CUSTOMER → ORDER  1 to Many  One customer can place multiple orders 
 + ORDER → ORDER_ITEM  1 to Many  One order can contain multiple products 
 + ORDER_ITEM → PRODUCT  Many to 1  Many order items can refer to the same product 
 + PRODUCT → PRODUCT_TYPE  Many to 1  Many products share a type (thrifted/handmade) 
 + PRODUCT → INVENTORY  1 to 1  Each product has exactly one inventory record 
 + ORDER → PAYMENT  1 to 1  Each order has one payment record 
 + ORDER → SHIPPING  1 to 1  Each order has one shipping record 
