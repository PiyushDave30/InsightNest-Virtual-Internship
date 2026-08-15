# Raw Data — [Ecommerce Dataset](ecommerce.csv)

## Overview

- **Rows:** 1,000 transaction-level records
- **Date range:** January 1, 2024 – December 30, 2025
- **Grain:** One row per order (order-level, not line-item level)

## Data Quality

Verified directly from the source file before building the dashboard:

- **Nulls:** 0 across all 24 columns
- **Duplicate rows:** 0
- **Duplicate `order_id`:** 0 (each order appears exactly once)
- **Calculated field formulas verified:**
  - `gross_amount` = `quantity` × `unit_price` ✅
  - `discount_amount` = `gross_amount` × `discount_pct` ✅
  - `net_revenue` = `gross_amount` − `discount_amount` ✅
  - `profit` = `net_revenue` − (`unit_cost` × `quantity`) ✅
- Categorical columns checked for consistent spelling (no case/typo variants)

## Column Dictionary

| Column | Type | Description |
|---|---|---|
| `order_id` | Text | Unique order identifier |
| `order_date` | Date | Date the order was placed |
| `customer_id` | Text | Unique customer identifier |
| `customer_segment` | Text | Consumer, Corporate, or Home Office |
| `product_id` | Text | Unique product identifier |
| `category` | Text | Product category (Electronics, Fashion, Sports, Home & Kitchen, Beauty, Books) |
| `sub_category` | Text | Product sub-category |
| `quantity` | Integer | Units purchased in the order |
| `unit_price` | Decimal | Selling price per unit before discount |
| `unit_cost` | Decimal | Cost per unit to the business |
| `discount_pct` | Decimal | Discount applied, as a fraction (e.g., 0.10 = 10%) |
| `gross_amount` | Decimal | `quantity × unit_price` (before discount) |
| `discount_amount` | Decimal | Discount value in currency |
| `net_revenue` | Decimal | Revenue after discount (`gross_amount − discount_amount`) |
| `profit` | Decimal | `net_revenue − (unit_cost × quantity)` |
| `payment_method` | Text | Credit Card, Debit Card, PayPal, Digital Wallet, Cash on Delivery |
| `marketing_channel` | Text | Organic Search, Paid Search, Email, Social, Direct, Affiliate |
| `shipping_mode` | Text | Same-Day, Standard, Express |
| `shipping_cost` | Decimal | Shipping cost for the order |
| `delivery_days` | Integer | Days taken to deliver |
| `country` | Text | Customer's country |
| `region` | Text | State/region within the country |
| `city` | Text | Customer's city |
| `is_returned` | Boolean | Whether the order was returned (TRUE/FALSE) |

## Dataset-Level Summary (verified from raw data)

| Metric | Value |
|---|---|
| Total Revenue | ₹236,764.29 |
| Total Profit | ₹66,190.66 |
| Total Cost | ₹170,573.63 |
| Total Orders | 1,000 |
| Total Customers | 326 |
| Total Quantity | 1,487 |
| Profit Margin % | 27.96% |
| Avg Selling Price | ₹169.78 |
| Return Rate % | 8.20% (82 returned orders) |
| Revenue Lost to Returns | ₹18,366.83 |
| Profit Lost to Returns | ₹5,117.65 |

### Revenue Share by Category
| Category | Revenue Share | Profit Share |
|---|---|---|
| Electronics | 53.23% | 30.84% |
| Home & Kitchen | 16.04% | 21.64% |
| Sports | 14.76% | 17.23% |
| Fashion | 11.17% | 20.95% |
| Beauty | 4.22% | 8.76% |
| Books | 0.58% | 0.57% |

### Return Rate by Category
| Category | Return Rate |
|---|---|
| Fashion | 14.16% |
| Electronics | 8.73% |
| Beauty | 7.48% |
| Sports | 5.22% |
| Books | 3.57% |
| Home & Kitchen | 3.23% |
