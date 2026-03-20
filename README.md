# Real-Time ELT Pipeline in Microsoft Fabric - OpenSky Air Traffic Monitoring

## Problem Statement
The goal of this project is to build a near-real-time ELT pipeline in Microsoft Fabric using medallion architecture to monitor air traffic over a selected geographic area.

## Architecture
- Source: OpenSky REST API
- Ingestion: Fabric Eventstream
- Storage: Eventhouse / KQL Database
- Bronze: `opensky_raw`
- Silver: `opensky_silver`
- Gold: `opensky_gold`

<img width="1004" height="283" alt="image" src="https://github.com/user-attachments/assets/9458bfb2-d82c-4465-89a0-ecc2d7478e33" />


## Bronze Layer
Raw JSON snapshots from OpenSky API are ingested into `opensky_raw`.

## Silver Layer
The `states` array is expanded into structured flight-level records in `opensky_silver`.

## Gold Layer
Aggregated metrics are calculated and stored in `opensky_gold`, including:
- number of active aircraft by country
- average velocity by country

## Data Quality Risks
1. Duplicate aircraft across snapshots
2. Missing or null values
3. Snapshot inconsistency and API latency

## Technologies
- Microsoft Fabric
- Eventstream
- Eventhouse
- KQL

## Files
- `opensky_pipeline.kql` - reproducible KQL script
- `architecture.png` - high-level architecture
- `erd.png` - logical ERD
