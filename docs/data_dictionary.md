# Data Dictionary

## hospitals

| Column | Description |
|---|---|
| `facility_id` | Unique CMS identifier for the hospital. Primary key. |
| `facility_name` | Hospital name. |
| `address` | Hospital street address. |
| `city` | Hospital city. |
| `state` | Two-character state or territory code. |
| `zip_code` | Hospital ZIP code. |
| `county` | County or parish. |
| `hospital_type` | CMS hospital type. |
| `hospital_ownership` | Hospital ownership category. |
| `emergency_services` | Indicates whether the hospital provides emergency services. |
| `overall_rating` | Original CMS overall hospital rating. |
| `hospital_source` | Source dataset used to create the hospital record. |
| `overall_rating_numeric` | Numeric representation of the overall rating used for analysis. |

## measures

| Column | Description |
|---|---|
| `measure_id` | Unique CMS quality-measure identifier. Primary key. |
| `measure_name` | Name of the CMS quality measure. |
| `condition` | Condition or clinical category associated with the measure. |

## hospital_measures

| Column | Description |
|---|---|
| `facility_id` | CMS hospital identifier. Foreign key to `hospitals`. |
| `measure_id` | CMS quality-measure identifier. Foreign key to `measures`. |
| `score_raw` | Original reported measure score. |
| `score_numeric` | Numeric representation of the measure score used for analysis. |
| `sample_raw` | Original reported sample value. |
| `sample_numeric` | Numeric representation of the sample value where available. |
| `footnote` | CMS-provided footnote or reporting note. |
| `start_date` | Beginning of the measure reporting period. |
| `end_date` | End of the measure reporting period. |

### Keys

The `hospital_measures` table uses a composite primary key:

`facility_id + measure_id + start_date + end_date`

This allows the same hospital and measure to appear across different reporting periods.