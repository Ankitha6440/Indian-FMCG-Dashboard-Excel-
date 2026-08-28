# Indian FMCG Retail — Sales, Customer & Inventory Dataset

A synthetic transaction-level dataset simulating one year (Jan–Dec 2024) of FMCG (Fast-Moving Consumer Goods) retail activity across major Indian cities. It combines sales, customer, and inventory information in a single table, and ships with a pre-built pivot table and dashboard for quick exploration.

## File Contents

The workbook (`Indian_FMCG_Retail_Sales__Customer__Inventory_dataset.xlsx`) has three sheets:

| Sheet | Description |
|---|---|
| `DATA` | The raw transaction-level dataset (100,000 rows × 21 fields) |
| `Pivot Table` | A pivot summary built from the raw data |
| `Dashboard` | A visual dashboard (charts + slicers) built on top of the pivot data |

## Data Dictionary (`DATA` sheet)

| Column | Type | Description |
|---|---|---|
| `Invoice_ID` | Integer | Unique identifier for each transaction |
| `Invoice_Date` | Datetime | Date and time of the transaction (Jan 1 – Dec 30, 2024) |
| `City` | Text | City where the transaction occurred |
| `Store_Format` | Text | Store type — `Express`, `Super`, or `Hyper` |
| `Category` | Text | Product category (e.g. `Grocery`, `Snacks`, `Dairy`) |
| `Brand` | Text | Product brand |
| `Channel` | Text | Sales channel — `Online`, `Offline`, or `Omnichannel` |
| `Payment_Mode` | Text | Payment method — `Cash`, `Card`, `UPI`, or `Wallet` |
| `Units` | Integer | Number of units sold in the transaction |
| `Cost_Price` | Decimal | Cost price per unit (₹) |
| `Selling_Price` | Decimal | Selling price per unit (₹) |
| `Revenue` | Decimal | Total revenue for the transaction (₹) |
| `Cost` | Decimal | Total cost for the transaction (₹) |
| `Margin` | Decimal | Profit margin in ₹ (Revenue − Cost) |
| `Margin_%` | Decimal | Profit margin as a percentage of revenue |
| `Stock_On_Hand` | Integer | Inventory units on hand at the time of sale |
| `Reorder_Level` | Integer | Inventory threshold that triggers reordering |
| `Lead_Time_Days` | Integer | Supplier lead time, in days, for restocking |
| `Customer_Age` | Integer | Age of the purchasing customer (may be missing) |
| `Customer_Gender` | Text | Customer gender — `M`, `F`, `O`, or missing |
| `Loyalty_Flag` | Binary | `1` if the customer is enrolled in a loyalty program, else `0` |

> Note: a handful of trailing helper/calculation columns exist beyond `Loyalty_Flag` and are mostly blank — safe to ignore for analysis.

## Coverage & Scale

- **Rows:** 100,000 transactions
- **Time period:** January 1, 2024 – December 30, 2024
- **Cities (8):** Ahmedabad, Bengaluru, Chennai, Delhi, Hyderabad, Kolkata, Mumbai, Pune
- **Store formats (3):** Express, Super, Hyper
- **Categories (8):** Beverages, Dairy, Fruits, Grocery, Home Care, Personal Care, Snacks, Vegetables
- **Brands (8):** Amul, Britannia, HUL, ITC, Nestle, Parle, PepsiCo, Tata
- **Channels (3):** Online, Offline, Omnichannel
- **Payment modes (4):** Cash, Card, UPI, Wallet

## Suggested Uses

- **Sales analysis** — revenue/margin trends by city, category, brand, or channel
- **Customer analytics** — purchasing patterns by age, gender, and loyalty status
- **Inventory management** — stock levels vs. reorder points and supplier lead times
- **Dashboarding / BI practice** — build on top of the included pivot table and dashboard, or recreate them in Power BI / Tableau

## Notes on Data Quality

- This appears to be a **synthetic/generated** dataset (values follow smooth statistical patterns), useful for practice, demos, or teaching — not a real retailer's data.
- `Customer_Age` and `Customer_Gender` contain some missing values, which is realistic for point-of-sale systems where customer info isn't always captured.

## Quick Start

```python
import pandas as pd

df = pd.read_excel(
    "Indian_FMCG_Retail_Sales__Customer__Inventory_dataset.xlsx",
    sheet_name="DATA"
)

df.head()
df.groupby("City")["Revenue"].sum().sort_values(ascending=False)
```
