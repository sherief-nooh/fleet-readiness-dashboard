# Power BI version

The same fleet data modelled as a star schema in Power BI Desktop.

| Table | Grain | Rows |
|---|---|---:|
| `dim_vehicle` | One vehicle | 200 |
| `dim_date` | One month, with Before / After period | 12 |
| `fact_usage` | Vehicle × month: km, fuel, days available | 2,400 |
| `fact_maintenance` | One workshop job | 1,467 |
| `fact_pm` | One preventive service due | 931 |

Relationships: `dim_vehicle[vehicle_id]` and `dim_date[month_date]` filter all three fact tables (one-to-many, single direction).

- `measures.dax`: calculated columns and measures, including the fuel exception flag (vehicle above its type median by 15%, calculated in DAX with `MEDIANX`)
- `fleet_theme.json`: report theme
- `fleet_readiness.pbix`: the report
