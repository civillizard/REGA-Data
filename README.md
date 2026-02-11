# REGA Real Estate Data Download

## Status: Complete (46/46 datasets)

## Source
- **Platform**: Saudi National Open Data Platform (open.data.gov.sa)
- **Organization**: الهيئة العامة للعقار (REGA - Real Estate General Authority)
- **Total Datasets**: 46
- **Data Type**: مؤشرات صفقات البيع (Sales Transaction Indicators) + مؤشرات الايجار (Rental Indicators)

## Data Categories
1. **Sales Transaction Indicators (2024-2025)**: Quarterly data by region
   - Eastern Region, Riyadh, Makkah, Madinah, Hail, Al Baha, etc.
2. **Rental Indicators**: City-level rental data by region
   - Covering all 13 administrative regions
3. **Special Datasets**: Property registration by gender (2024)

## CSV Data Fields
Each sales dataset contains:
- السنة (Year)
- الربع (Quarter number & name)
- المنطقة (Region)
- المدينة (City)
- الحي (Neighborhood)
- نوع العقار (Property Type: أرض/دور/etc)
- تصنيف العقار (Property Classification: سكني/تجاري)
- عدد الصكوك (Number of deeds)
- قيمة الصفقات (Transaction value in SAR)
- المساحة M2 (Area in square meters)
- متوسط سعر المتر (Average price per meter)
- الحد الأعلى/الأدنى لسعر المتر (Max/Min price per meter)

## Technical Documentation

### API Access (WAF Blocked for Direct Curl)
Direct API calls via curl are blocked by the platform's WAF.
Must use browser automation (Playwright) to access data.

### API Endpoints (Work via Browser)
```
# Get dataset metadata + resource IDs
GET https://open.data.gov.sa/api/datasets/{datasetID}

# Download file
GET https://open.data.gov.sa/data/api/v1/datasets/{datasetID}/resources/{resourceID}/download
```

### Example
```
Dataset ID: 64e40f14-356b-4d1c-b3c9-a3d107eb1927
CSV Resource ID: 8a676f5a-1891-4be5-80b2-9656731927e4
XLSX Resource ID: e1ab3247-e2bc-4930-9d6b-8483fcfadc4a

Download URL:
https://open.data.gov.sa/data/api/v1/datasets/64e40f14-356b-4d1c-b3c9-a3d107eb1927/resources/8a676f5a-1891-4be5-80b2-9656731927e4/download
```

## Files
- `datasets.json` - Complete catalog of all 46 datasets with IDs
- `Sales-transaction-indicators-in-*.csv` - Quarterly sales by region (2024-2025)
- `Rental-indicators-for-cities-in-*.csv` - Rental data by region (2019-2024, all 13 regions)
- `Registered-Real-Estate-by-Gender-2024.csv` - Property registration by gender
- `quarter-report-SI.csv` - Consolidated quarterly sales report (32,731 rows)
- `charts/` - Infographic visualizations

## Data Summary
- **46 CSV files** — all downloaded and verified
- **~51,000 total data rows** across all files
- **13 rental region files**: ~18,700 rows (Riyadh 4,486 | EP 2,383 | Qassim 2,241 | Makkah 2,066 | others 614-1,943)
- **27 sales transaction files**: quarterly breakdowns by region

## Cleanup Notes
- Eastern Province rental CSV originally had 1,028,621 comma-only blank rows from the open data platform export (8.4 MB). Cleaned to 2,384 actual data rows (202 KB) on 2026-02-11.

Last updated: 2026-02-11
