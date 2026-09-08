# Part 2: Tesla Deaths Exploratory Data Analysis

## Project Overview

This project is Part 2 of the AIML Capstone. The objective is to analyze the Tesla deaths dataset and study accident patterns, death events, Tesla driver and occupant fatalities, cyclist/pedestrian involvement, other vehicle collisions, Tesla model-wise distribution, and Autopilot-related fatality records.

The analysis was performed using Python, Pandas, NumPy, and Matplotlib inside a Jupyter Notebook.

## Dataset

Dataset used:

```text
Tesla - Deaths.csv
```

Initial dataset shape:

```text
Rows: 307
Columns: 24
```

After cleaning:

```text
Rows: 295
```

## Project Folder Structure

```text
Part2_Tesla_Deaths_EDA/
│
├── README.md
│
├── data/
│   └── Tesla - Deaths.csv
│
├── outputs/
│   ├── accidents_per_year.png
│   ├── deaths_per_year.png
│   ├── deaths_distribution.png
│   ├── country_distribution.png
│   ├── state_distribution.png
│   ├── model_distribution.png
│   ├── deaths_by_model.png
│   ├── autopilot_claimed_vs_verified.png
│   ├── verified_autopilot_deaths_by_year.png
│   ├── tesla_deaths_cleaned.csv
│   └── summary_metrics.csv
│
└── Part2_Tesla_Deaths_EDA.ipynb
```

## Technologies Used

* Python
* Jupyter Notebook
* Pandas
* NumPy
* Matplotlib

## Data Cleaning Steps

The following cleaning steps were performed:

1. Removed extra spaces from column names.
2. Removed duplicate rows.
3. Removed blank or invalid rows.
4. Dropped unnecessary columns:

   * `Unnamed: 16`
   * `Unnamed: 17`
   * `Source`
   * `Note`
   * `Deceased 1`
   * `Deceased 2`
   * `Deceased 3`
   * `Deceased 4`
5. Converted numeric columns into numeric datatype.
6. Converted the `Date` column into datetime format.
7. Created a clean `Final_Year` column.
8. Created derived columns for easier analysis:

   * `Tesla_Driver_Died`
   * `Tesla_Occupant_Died`
   * `Cyclist_or_Ped_Involved`
   * `Other_Vehicle_Involved`
   * `Autopilot_Claimed_Flag`
   * `Verified_Autopilot_Death_Flag`

## Why Deceased Columns Were Removed

The columns `Deceased 1`, `Deceased 2`, `Deceased 3`, and `Deceased 4` were removed because they contained deceased-person identifiers/names, had very high missing values, and were not required for the numerical EDA objectives.

The analysis focused on aggregate accident and fatality columns such as:

* `Deaths`
* `Tesla driver`
* `Tesla occupant`
* `Cyclists/ Peds`
* `Other vehicle`
* `Model`
* `Autopilot claimed`
* `Verified Tesla Autopilot Deaths`

## Key Results

Final cleaned dataset:

```text
Total accident cases: 295
Total deaths: 353
Average deaths per accident: 1.20
```

Tesla driver death analysis:

```text
Accidents where Tesla driver died: 117
Total Tesla driver deaths: 117
Percentage of accidents where Tesla driver died: 39.66%
```

Tesla occupant death analysis:

```text
Accidents where one or more Tesla occupants died: 43
Total Tesla occupant deaths: 48
Proportion of events with Tesla occupant death: 14.58%
```

Cyclist/pedestrian death analysis:

```text
Accidents involving cyclist/pedestrian deaths: 44
Total cyclist/pedestrian deaths: 46
Percentage of accidents involving cyclist/pedestrian deaths: 14.92%
```

Tesla and cyclist/pedestrian combined fatality analysis:

```text
Accidents involving Tesla driver/occupant death along with cyclist/pedestrian death: 1
Total Tesla driver/occupant + cyclist/pedestrian deaths in those accidents: 2
```

Other vehicle collision analysis:

```text
Accidents involving other vehicles: 110
Total other vehicles involved: 130
Percentage of accidents involving other vehicles: 37.29%
```

Autopilot claimed analysis:

```text
Accidents where Autopilot was claimed: 35
Deaths in Autopilot-claimed accidents: 43
Percentage of accidents where Autopilot was claimed: 11.86%
```

Verified Tesla Autopilot death analysis:

```text
Events with verified Tesla Autopilot deaths: 16
Total verified Tesla Autopilot deaths: 19
Percentage of events with verified Autopilot deaths: 5.42%
```

## Tesla Model Analysis

The model column had many missing or unknown values.

After cleaning:

* Unknown model had the highest number of records.
* Among known models, Model S had the highest number of fatal events.
* Model 3 was the second highest among known models.
* Model X and Model Y had lower event counts.

## Important Data Interpretation Note

The column `TSLA+cycl / peds` was inspected separately. It was not directly used for cyclist/pedestrian involvement because it contained positive values even when the `Cyclists/ Peds` column was zero.

Therefore, the combined Tesla and cyclist/pedestrian fatality condition was calculated manually using:

* `Tesla driver`
* `Tesla occupant`
* `Cyclists/ Peds`

## Output Charts

The notebook generates the following charts:

```text
accidents_per_year.png
deaths_per_year.png
deaths_distribution.png
country_distribution.png
state_distribution.png
model_distribution.png
deaths_by_model.png
autopilot_claimed_vs_verified.png
verified_autopilot_deaths_by_year.png
```

## Output Files

The project generates:

```text
tesla_deaths_cleaned.csv
summary_metrics.csv
```

These files are saved inside the `outputs` folder.

## Limitations

The analysis has the following limitations:

1. Several fields contained missing values.
2. Many records had unknown or unreported Tesla model information.
3. The dataset records fatal accidents only, not all Tesla accidents.
4. The dataset does not include total Tesla miles driven.
5. The dataset does not include Autopilot miles driven.
6. Due to missing exposure data, true risk rate per mile cannot be calculated.
7. Autopilot claimed and verified Autopilot deaths are different and should not be treated as the same measure.

## Conclusion

The Tesla deaths dataset was cleaned and analyzed to understand fatal accident patterns and Autopilot-related death records.

The cleaned dataset contained 295 accident cases and 353 total deaths. Autopilot was claimed in 35 events, representing 11.86% of the accident cases. Verified Tesla Autopilot deaths were found in 16 events, representing 5.42% of the cases.

The analysis shows that most fatal Tesla accident cases in this dataset were not verified Autopilot death events. However, because the dataset does not include total miles driven or Autopilot usage miles, it cannot prove whether Autopilot increases or decreases road safety risk. The analysis describes patterns only within the available fatal accident records.
