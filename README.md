# DeedMapper Web App

A web application for viewing historical land records from DeedMapper (.mbl files) with optional overlay on USGS topo maps.

## Files

- `deed-mapper-app.html` - The main web application
- `NC_Iredell.mbl` - Database of historical land surveys (Iredell County, NC area)

## How to Use

1. Open `deed-mapper-app.html` in a web browser (Chrome recommended)
2. Click "Choose File" and select your `.mbl` database file
3. Plots will display on the canvas with the deeds table on the right

## Features

- **Plot Display**: Shows land survey boundaries with metes and bounds
- **Interactive Table**: Click rows to highlight and center on plots
- **Search**: Filter table by ID, name, date, etc.
- **Sortable Columns**: Click column headers to sort
- **View Modal**: Click "View" link for detailed single-plot view
- **Type Filtering**: Show/hide Surveys, Deeds, or Other record types
- **Customizable Labels**: Choose which fields appear in plot labels
- **Geographic Mode**: Overlay plots on USGS topo maps

## Key Settings

### Scale Multiplier: 0.6
Controls the size of individual plot shapes. This value correctly scales metes and bounds measurements (poles, chains) for display.

### Geographic Mode Settings

| Setting | Value | Description |
|---------|-------|-------------|
| Anchor Plot ID | Rowan-3090 | Reference plot for positioning |
| Anchor Lat | 35/55/25 | Latitude in dd/mm/ss format |
| Anchor Lon | -80/49/27 | Longitude in dd/mm/ss format |
| Geo Scale | 1.667 | Converts MBL units to feet (= 1/0.6) |
| Rotation | 7 | Degrees clockwise for magnetic declination correction |

### Why These Values?

- **Geo Scale = 1.667**: Mathematically derived as 1 / Scale Multiplier. The MBL loc coordinates appear to be in feet.
- **Rotation = 7 degrees**: Compensates for magnetic declination change from 1780s to present. Original surveys used magnetic north; the topo map uses true north.

## Coordinate System Notes

- **Metes and Bounds Units**:
  - 1 pole (p) = 16.5 feet
  - 1 chain (c) = 66 feet
  - 1 rod (r) = 16.5 feet

- **Geographic Conversion** (at ~36°N latitude):
  - 1 degree latitude ≈ 364,000 feet
  - 1 degree longitude ≈ 294,000 feet

## Adjusting Position on Map

| To Move | Adjust |
|---------|--------|
| North | Increase latitude (e.g., 35/55/25 → 35/55/35) |
| South | Decrease latitude (e.g., 35/55/25 → 35/55/15) |
| East | Decrease longitude magnitude (e.g., -80/49/27 → -80/49/17) |
| West | Increase longitude magnitude (e.g., -80/49/27 → -80/49/37) |

Approximate scale: 1 second ≈ 100 feet (lat) or 80 feet (lon)

## Future Improvements to Consider

- Additional basemap options (satellite, street map)
- Export to GeoJSON or KML
- Save/load settings
- Print-friendly layout
- Neighbor relationship visualization

## Technical Details

- Built with Leaflet.js for mapping
- USGS National Map topo tiles for basemap
- Single-file HTML application (no server required)
- Works offline except for topo map tiles

---
*Created with Claude Code, February 2025*
