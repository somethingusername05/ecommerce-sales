# Ecommerce Sales Dashboard

A Power BI dashboard analyzing ecommerce order, shipping, and profitability data for a US-based retailer.

## Overview

This project explores order-level ecommerce transaction data to surface trends in sales, profit, delivery performance, and regional demand. The dashboard is built in Power BI and backed by a single flat transaction dataset plus a US state geo-lookup table for map visuals.

## Repository Structure

```
ecommerce-sales-dashboard/
├── data/
│   ├── ecommerce_data.csv           # Primary order-level dataset (raw)
│   ├── ecommerce_data_excel.xlsx    # Same dataset in Excel format
│   └── us_state_long_lat_codes.csv  # US state lat/long lookup, used for map visuals
├── dashboard/
│   └── Ecommerce_Sales_Dashboard.pbix   # Power BI report file
├── assets/
│   └── Final_Back.jpg               # Dashboard background/theme image
├── docs/
│   └── power_bi_import_notes.md     # Data-type gotchas to check on refresh
└── README.md
```

## Data

**`ecommerce_data.csv` / `ecommerce_data_excel.xlsx`** — ~113,000 rows, one row per order line item. Key fields:

| Field | Description |
|---|---|
| `customer_id`, `customer_first_name`, `customer_last_name` | Customer identity |
| `customer_segment` | Consumer / Corporate / Home Office |
| `customer_city`, `customer_state`, `customer_country`, `customer_region` | Customer geography (Central, East, South, West) |
| `category_name`, `product_name` | Product info (Office Supplies, Furniture, Technology) |
| `order_date`, `ship_date` | Order and shipment dates |
| `delivery_status`, `shipping_type` | Delivery outcome and shipping method |
| `days_for_shipment_scheduled`, `days_for_shipment_real` | Scheduled vs. actual shipping days |
| `order_item_discount`, `sales_per_order`, `order_quantity`, `profit_per_order` | Order economics |

**`us_state_long_lat_codes.csv`** — state code, latitude, longitude, and full state name, used to plot customers/sales geographically in Power BI.

## Dashboard

`dashboard/Ecommerce_Sales_Dashboard.pbix` contains the full Power BI report (data model, measures, and report pages). Open with Power BI Desktop.

## Setup

1. Clone the repo.
2. Open `dashboard/Ecommerce_Sales_Dashboard.pbix` in Power BI Desktop.
3. If prompted, repoint the data source to the local `data/` folder.
4. **Before refreshing**, read `docs/power_bi_import_notes.md` — the `order_date` column needs to be explicitly typed as Date on import or several date-based visuals will break.

## Notes

- `ecommerce_data.csv` and `ecommerce_data_excel.xlsx` contain the same data in two formats; only one needs to be loaded into the model.
- Large data files (`ecommerce_data.csv` ~25 MB, `ecommerce_data_excel.xlsx` ~14 MB) — consider [Git LFS](https://git-lfs.com/) if GitHub flags them for size, since GitHub's soft limit is 50 MB per file but repos get slow with large binary/CSV files tracked normally.
