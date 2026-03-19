# B13 Supplements Store Starter

This is a functional starter project for a modern supplement e-commerce website built with **Next.js + Prisma + SQLite**.

## Included
- Modern storefront homepage
- Product detail page
- Cart and checkout UI
- Customer account UI
- Admin panel
- Product management page
- Discount management page
- Inventory and stock movement page
- Prisma database schema
- Excel import from `Leader pricelist Martins LV.xlsx`
- Stock movement logging model for accounting support

## Main business features
- Product base price from Excel
- Retail price stored separately
- Sale price for single products
- Category-level discount percentage
- Stock quantity and reserved quantity fields
- Stock movement history with:
  - date/time
  - reference number
  - customer/recipient
  - notes
  - previous and new stock level

## Tech stack
- Next.js 15
- React 19
- Prisma ORM
- SQLite for quick local start
- XLSX import parser

## Setup
1. Copy `.env.example` to `.env`
2. Install dependencies:
   ```bash
   npm install
   ```
3. Generate Prisma client:
   ```bash
   npx prisma generate
   ```
4. Create database:
   ```bash
   npx prisma migrate dev --name init
   ```
5. Import Excel catalog:
   ```bash
   npm run import:excel
   ```
6. Start development server:
   ```bash
   npm run dev
   ```

## Important note
This is a strong working starter, not a fully finished production deployment. Before going live, you should still add:
- authentication
- payment gateway integration
- shipping integration
- email sending
- VAT rules for checkout
- image upload storage
- order placement logic connected to real cart/session
- admin form actions for editing directly in UI
- security hardening and validation

## Excel mapping used
The importer detects category blocks and product rows from your Excel structure:
- Column A: SKU / product code
- Column B: product name / category title rows
- Column E: size
- Column F: ALV 0% base price

When imported:
- base price = Excel ALV 0% price
- retail price = base price x 2 (default starter logic, editable later)
- category = nearest category header block above product rows

## Accounting support
The inventory system is designed so month-end bookkeeping is easier:
- incoming stock
- outgoing stock
- damaged stock
- manual corrections
- recipient/customer reference
- order/reference number
- movement history export ready structure
