# Healthcare Operations & Billing Dashboard

A Power BI dashboard that gives hospital administrators one place to track billing, patient volume, and care efficiency across multiple facilities.

![Dashboard](dashboard.png)

## Business Question
Where does billing concentrate across hospitals, admission types, and age groups, and how efficiently are patients moving through care?

## Key Metrics
| KPI | Value |
|---|---|
| Total Billing Amount | 1.42bn |
| Average Billing Amount | 25.54K |
| Doctor-to-Patient Ratio | 0.92 |
| Average Length of Stay | 15.50 days |

## What the Dashboard Shows
- **Billing by hospital and admission type** (Elective, Emergency, Urgent) as a stacked bar chart
- **Total vs. average billing by age category**, so volume and per-case cost can be compared side by side
- **Monthly patient volume** trend across the year
- **Doctor-to-patient ratio by blood type**
- **Slicers** for medication, medical condition, test results, admission type, and blood type

## Data Model
Star schema built in Power BI: `Fact Healthcare` connected to `Dim Patients` and `Dim Hospital`, so every visual filters consistently.

## DAX Highlight
Average Length of Stay is an iterator measure, because the number of days per patient doesn't exist as a column and has to be calculated row by row:

```
Average Length of Stay =
AVERAGEX(
    'Dim Patients',
    DATEDIFF('Dim Patients'[Date of Admission], 'Dim Patients'[Discharge Date], DAY)
)
```

## Observations
- The Old and Adult age categories account for most of the total billing.
- Admissions are not flat across the year, with a clear dip in February and a peak in the summer months.

## Tools
Power BI, DAX, Power Query, data modeling (star schema)

## Dataset
[Add the dataset source link here]
