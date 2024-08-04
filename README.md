# Inventory-Service

## Architecture
<p align="center">
<img src= "https://github.com/user-attachments/assets/c4e6a506-cdce-48a4-b86b-17381d908d71" align = "center">
</p>

## Microservices Involved
<ol>
<li> Inventory Management Service : 
  <ul>
    <li>
      Manages the list of products and checks their availability.
    </li>
    <li>
      Updates inventory levels when an order is placed or canceled.
    </li>
  </ul>
    </li>

<li> Warehouse Management Service :
    <ul> 
      <li>
        Stores detailed information about the stock in different warehouses.</li>
    <li> Provides data to the Inventory Management Service to verify stock availability. </li>
        </ul>
<li> Order Management Service :
  <ul>
    <li> Handles order placement and cancellation.</li>
    <li>Coordinates with Inventory Management to ensure product availability before processing orders.</li>
  </ul>
  </li>
<li>Invoice Generation Service :
  <ul>
    <li>
    Generates invoices when an order is successfully placed.</li>
    <li> Provides downloadable invoice files.</li>
  </ul>
</li>
<li> Front-end UI :
  <ul>
    <li> A simple HTML/CSS user interface for interacting with the services. </li> 
    <li> Includes forms to place orders, check inventory, and download invoices. </li>
  </ul>
</li>
</ol>

## Design the Data Flow and Interactions

- Request Flow :
    - User places an order via the UI.
    - Order Management Service verifies inventory via Inventory Management Service.
    - Inventory Management Service checks stock from Warehouse Management Service.
    - If available, the order is confirmed, and Inventory Management updates the stock.
    - Invoice Generation Service creates and stores the invoice.
    - User downloads the invoice via UI.
- Error Handling :
    - If inventory is insufficient, notify the Order Management Service to cancel the order and update the user.
