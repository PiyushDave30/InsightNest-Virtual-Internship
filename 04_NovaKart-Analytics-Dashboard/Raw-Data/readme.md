# 📦 Raw Data

This folder contains the source dataset used for the NovaKart Analytics Dashboard project.

## File

**`NovaKart_Analyst_Practice_Pack.xlsx`**

An Excel workbook containing the original raw data as received, alongside the cleaned/transformed tables produced during the Power Query cleaning process (Tier 1 — see the [main project README](../README.md#tier-1--data-cleaning) for the full cleaning methodology).
 
## Workbook Contents

The file is organized into the following sheets:

| Sheet | Purpose |
|---|---|
| `START HERE` | Project brief and instructions as originally provided |
| `Data Dictionary` | Field-level definitions for every table |
| `Questions` | The full list of business questions the analysis answers |
| `orders` | Raw transaction-level order data |
| `customers` | Raw customer master data |
| `products` | Product catalog |
| `returns` | Return records |

## Data Dictionary

### `orders`
| Field | Type | Description |
|---|---|---|
| order_id | Text | Unique order identifier |
| customer_id | Text | Links to `customers.customer_id` |
| product_id | Text | Links to `products.product_id` |
| order_date | Text/Date | Date the order was placed (mixed formats in raw data — see cleaning notes) |
| quantity | Number | Units ordered |
| unit_price | Number | Price per unit at time of order |
| discount_pct | Number | Discount applied (mixed scale in raw data — see cleaning notes) |
| order_status | Text | Delivered / Cancelled / Returned |
| channel | Text | Mobile App / Website / Marketplace |
| payment_method | Text | UPI / Cash on Delivery / Credit Card / Debit Card / Wallet / Net Banking |
| delivery_days | Number | Days taken to deliver the order |

### `customers`
| Field | Type | Description |
|---|---|---|
| customer_id | Text | Unique customer identifier |
| city | Text | Customer's city (inconsistent casing/whitespace in raw data — see cleaning notes) |
| state | Text | Customer's state |
| segment | Text | New / Premium / Returning |
| email | Text | Customer email (some blanks) |

### `products`
| Field | Type | Description |
|---|---|---|
| product_id | Text | Unique product identifier |
| product_name | Text | Product name |
| category | Text | Electronics / Apparel / Fitness / Home |
| sub_category | Text | e.g. Womenswear, Menswear, Footwear, Wearables, Audio, etc. |
| cost_price | Number | Cost to NovaKart per unit |
| list_price | Number | Selling price per unit before discount |

### `returns`
| Field | Type | Description |
|---|---|---|
| order_id | Text | Links to `orders.order_id` |
| return_date | Date | Date the return was filed |
| return_reason | Text | e.g. Size issue, Not as described, Changed mind, Defective product, Late delivery |
| refund_status | Text | Status of the refund |

## Raw Data Quality Issues (Resolved During Cleaning)

The dataset was intentionally provided with realistic data quality problems, all diagnosed and resolved in Power Query before any analysis was performed:

| Issue | Detail | Resolution |
|---|---|---|
| Duplicate rows | Exact duplicate order rows present | Removed |
| Mixed date formats | `order_date` mixed `YYYY-MM-DD` and `DD-MM-YYYY` | Standardized via conditional parsing |
| Inconsistent discount scale | `discount_pct` mixed fractions (0.15) and whole numbers (15) | Rescaled to a single consistent percentage |
| Inconsistent city names | 60 distinct raw values for what were really 12 cities | Trimmed and standardized casing |
| Invalid quantities | 37 rows with quantity ≤ 0 | Removed |
| Blank fields | `payment_method`, `delivery_days`, `email` had blanks | Left blank deliberately (not imputed) to avoid distorting downstream analysis |
| Orphan customer references | 17 orders referenced a customer_id with no matching customer record | Kept via Left Join (not dropped) to preserve real revenue |

## Row Counts

| Stage | orders | customers | products | returns |
|---|---|---|---|---|
| Raw | 8,853 | 2,400 | 25 | 671 |
| After cleaning | 8,276 | 2,400 | 25 | 671 |

Full reasoning behind each cleaning decision is documented in the [main project README](../README.md#tier-1--data-cleaning) and the [Business Questions document](../Business-Questions.md).
