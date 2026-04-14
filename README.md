# Project Fathom

ML-driven shower detection and water cost analytics using Home Assistant sensor data.
Why Fathom? I wanted something water-adjacent and I am trying to "fathom" a way to
accurately predict shower usage from Home Assistant data. That's why.

## What This Project Does

Uses indirect sensor data (bathroom humidity, temperature, and whole-house water 
flow) to detect when specific showers are running — without per-shower water 
sensors. From that inference, calculates per-shower water cost, heating cost, 
and percentage of total household water consumption.

## Project Phases

- **Phase 1** ✅ — Data pipeline: InfluxDB + Grafana connected to Home Assistant
- **Phase 2** 🚧 — ML modeling: shower detection classifier in Jupyter notebooks
- **Phase 3** ⏳ — HA integration: live virtual sensors and dashboard

## Tech Stack

- Home Assistant OS
- InfluxDB 2.7
- Grafana
- Docker / Docker Compose
- Python / Jupyter (Phase 2)
- scikit-learn (Phase 2)

## Prerequisites

- Docker and Docker Compose
- Home Assistant with sensors for humidity, temperature, and water flow

## Quick Start

1. Clone this repo
2. Copy `.env.example` to `.env` and fill in your values
3. Pre-create data directories and set permissions:
```bash
   mkdir -p /mnt/user/appdata/influx/data
   mkdir -p /mnt/user/appdata/influx/config
   mkdir -p /mnt/user/appdata/grafana/data
   chown -R 1000:1000 /mnt/user/appdata/influx
   chown -R 472:472 /mnt/user/appdata/grafana
```
4. Start the stack:
```bash
   docker compose up -d
```
5. Access InfluxDB at `http://your-server-ip:8086`
6. Access Grafana at `http://your-server-ip:3000`
7. Connect Home Assistant via Settings → Integrations → InfluxDB (get API token from Influx first)
8. Import the Grafana dashboard from `grafana/dashboards/` (make sure you adjust for your bathroom count and entity names from your Home Assistant instance!)

## Project Status
Phase 1 complete. Data pipeline live and collecting. Phase 2 begins after 
2-3 weeks of data collection.

## License
MIT
