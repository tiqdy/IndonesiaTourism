# Indonesia Tourism Analytics

An end-to-end data engineering and business intelligence project that integrates tourism statistics, weather data, and Google Trends to analyze tourism patterns across five Indonesian provinces.

The project covers the complete analytics workflow — from multi-source data collection and ETL processing to dimensional data modeling, PostgreSQL data warehousing, and interactive visualization in Power BI.

## Live Dashboard

**[View Interactive Power BI Dashboard](https://app.powerbi.com/view?r=eyJrIjoiNGI0Yzk1M2YtZWQ5ZS00ZDAxLTliYTQtYTgzNjNiNjM3NDNiIiwidCI6IjM0ODViOTYzLTgyYmEtNGE2Zi04MTBmLWI1Y2MyMjZmZjg5OCIsImMiOjEwfQ%3D%3D&pageName=fcde229a23533ed6d4b3)**

Explore the full interactive dashboard in Power BI, including tourism performance, seasonal patterns, weather relationships, and Google search interest.

## Project Overview

Tourism demand is influenced by more than historical visitor numbers. Seasonal weather conditions, hotel activity, and changes in online search interest can provide additional context for understanding when and why tourism activity changes.

**Indonesia Tourism Analytics** integrates tourism statistics, historical weather data, and Google Trends data from 2023–2025 to analyze tourism performance and external factors across five Indonesian provinces.

The final output is an interactive Power BI dashboard designed to provide useful insights for tourism agencies and hospitality industry stakeholders.

## Research Questions

This project focuses on the following research questions:

1. How are weather conditions associated with tourist visits across provinces?
2. Which months represent peak tourism seasons in each province?
3. Does Google search interest precede changes in actual tourist visits?
4. How do the relationships between weather and tourism differ across provinces?

## Data Sources

The project integrates three different data sources.

### Tourism Data

Tourism statistics are used to measure tourism activity and hospitality performance, including:

- International tourist visits (Wisman)
- Domestic tourist visits (Wisnus)
- Hotel Occupancy Rate (TPK)
- Average Length of Stay (RLM)

### Weather Data

Historical weather data provides environmental variables that may be associated with tourism activity:

- Average temperature
- Total monthly rainfall
- Rainfall category

Weather observations are mapped using representative locations for each province.

### Google Trends

Google Trends scores are used as an indicator of online search interest related to tourism destinations.

Lagged analysis is also used to examine whether changes in search interest occur before changes in actual tourist visits.

## Data Architecture

The analytical warehouse follows a **Star Schema** consisting of one fact table and three dimension tables.

### `dim_waktu`

Time dimension used for time-series and seasonal analysis.

- `id_waktu`
- `tahun`
- `bulan`
- `nama_bulan`
- `kuartal`
- `musim`

### `dim_provinsi`

Contains geographical information for the five provinces included in the analysis.

- `id_provinsi`
- `nama_provinsi`
- `kota_cuaca`
- `latitude`
- `longitude`
- `pulau`

### `dim_kategori_cuaca`

Contains rainfall classifications.

- `id_kategori`
- `kategori`
- `range_hujan`
- `min_mm`
- `max_mm`

### `fact_kunjungan_pariwisata`

Central fact table containing tourism, hospitality, weather, and search-interest measures.

- `id_fakta`
- `id_waktu`
- `id_provinsi`
- `id_kategori_cuaca`
- `jumlah_wisman`
- `jumlah_wisnus`
- `tpk`
- `rlm`
- `avg_suhu`
- `total_curah_hujan`
- `skor_trends`

## ETL Pipeline

The project follows an end-to-end ETL workflow:

```text
Tourism Data ──────┐
                   │
Weather Data ──────┼──> Extract ──> Transform ──> PostgreSQL ──> Power BI
                   │
Google Trends ─────┘
```

The pipeline performs:

- Multi-source data extraction
- Data cleaning and standardization
- Province mapping
- Date and time transformation
- Monthly weather aggregation
- Rainfall categorization
- Tourism metric integration
- Google Trends integration
- Data validation
- Dimensional modeling
- Data warehouse loading

## Power BI Dashboard

The Power BI dashboard is divided into two analytical pages to maintain a clear analytical flow and avoid repetitive visualizations.

### Page 1 — Performance & Seasonality

Provides an overview of tourism performance and seasonal patterns across provinces.

Key analyses include:

- Total tourist visits
- Domestic vs. international visitors
- Tourism trends from 2023–2025
- Provincial tourism performance
- Monthly seasonal patterns
- Peak tourism periods
- Hotel Occupancy Rate (TPK)
- Average Length of Stay (RLM)

### Page 2 — External Factors

Examines external factors that may be associated with changes in tourism demand.

Key analyses include:

- Rainfall vs. tourist visits
- Average temperature
- Google search interest
- Google Trends YoY growth
- Lagged Google Trends vs. tourist visits
- Province-level correlation analysis

## Key Dashboard Metrics

The dashboard includes several high-level KPIs:

- **Total Tourist Visits**
- **Domestic Tourist Visits**
- **International Tourist Visits**
- **Average TPK**
- **Average RLM**
- **Digital Interest Index**
- **Search Interest YoY Growth**
- **Average Rainfall**
- **Average Temperature**

## Dashboard Preview

> **[Open the Interactive Power BI Dashboard](https://app.powerbi.com/view?r=eyJrIjoiNGI0Yzk1M2YtZWQ5ZS00ZDAxLTliYTQtYTgzNjNiNjM3NDNiIiwidCI6IjM0ODViOTYzLTgyYmEtNGE2Zi04MTBmLWI1Y2MyMjZmZjg5OCIsImMiOjEwfQ%3D%3D&pageName=fcde229a23533ed6d4b3)**

## Technology Stack

### Data Engineering
- Python
- Pandas
- SQL
- PostgreSQL

### Data & APIs
- BPS Tourism Statistics
- Open-Meteo
- Google Trends

### Business Intelligence
- Microsoft Power BI
- DAX
- Power Query

### Development
- Git
- GitHub

## Project Purpose

This project demonstrates an end-to-end analytics workflow combining **data engineering, ETL, dimensional modeling, data warehousing, statistical analysis, and business intelligence**.

Rather than analyzing tourism statistics in isolation, the project integrates weather conditions and online search interest to provide additional context for understanding tourism demand across Indonesia.
