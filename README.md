# REGA Real Estate Data Download

## Status: In Progress

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
- `*.csv` - Downloaded data files

## Download Progress
- [x] Dataset catalog compiled (46 datasets)
- [x] Download URL structure identified
- [x] First file downloaded and verified
- [ ] Remaining 45 datasets

Last updated: 2026-01-17
