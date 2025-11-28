# GTFS Coverage (FME)

FME workspaces to analyse GTFS data and measure service coverage at stop level.

Originally built for **Blacktown LGA (NSW, Australia)** to find lots within a **400 m catchment of bus stops** where each stop has **at least one service per hour** in a chosen time window. The same logic can be reused for any LGA if you provide a different boundary and GTFS feed.

---

## What it does

- Reads GTFS, clips stops to the LGA boundary.
- Joins `stops`, `stop_times`, `trips`, `routes` to build a **stop–hour** table.
- Counts services per **stop + hour** for each day.
- Flags stops that meet a **minimum services per hour** rule across the time window.
- Writes outputs as **GPKG / SHP / XLSX**.

---

## Workspaces

### `GTFS_Coverage_Min1PerHour.fmw`

Checks which stops have **at least one service per hour** within the specified time window.

### `GTFS_Coverage_MinNPerHour.fmw`

Same logic, but with a parameter:

- `MinServicesPerHour` – minimum number of services per hour (e.g. 1, 2, 3+).

---

## Inputs

- Standard GTFS feed (`stops.txt`, `stop_times.txt`, `trips.txt`, `routes.txt`).
- LGA boundary layer (e.g. Blacktown LGA).
- User-specified:
  - GTFS folder/file,
  - output folder,
  - output format (**GPKG / SHP / XLSX**),
  - and `MinServicesPerHour` (for the N-version).

Outputs can be used in GIS (e.g. intersect with 400 m buffers and parcels) to support accessibility / Housing SEPP–style assessments.
